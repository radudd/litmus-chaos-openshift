# About

Many of the LitmusChaos experiments require elevated privileges to run resilience tests against pods or nodes in the cluster. Example of privilges required: privileged containers, privilege escalation, adding extra capabilities like SYS_ADMIN and NET_ADMIN, host access to mount CRIO socket.

In order to ensure that these LitmusChaos experiments can be executed in OpenShift, the service account that runs them will need to use a custom Security Context Constraint (SCC) which will contain there privileges.  

# Steps


Create SCC

```
oc apply -f  https://raw.githubusercontent.com/radudd/litmus-chaos-openshift/main/manifests/scc.yaml
```

Create the Role that allows using the SCC

```
oc apply -f  https://raw.githubusercontent.com/radudd/litmus-chaos-openshift/main/manifests/role.yaml
```

Finally create the RoleBinding

NOTE: Update namespace name in the manifests/rolebinding.yaml according to your configuration.

```
oc apply -f  https://raw.githubusercontent.com/radudd/litmus-chaos-openshift/main/manifests/rolebinding.yaml
```