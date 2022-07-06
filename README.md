This is a Teeraform IaC demonstration for setting up a hub and spoke environment in Azure.

The hub and spoke topology consists of on-premise network (ex. server located at the site) which is connected to a hub - a standalone virtual network. This hub is the ultimate management network of other networks which will compute the workload. In this demonstration, the hub connects only to two other spokes which are "vnet peered" from the hub. This means that communication between only the hub and only another spoke is available which can be tested via pinging. An Ubuntu image VM is configured to act as a virtual network appliance which faciliates traffic routing within the entire network.

Other important notes:
- Each network also has a gateway; traffic control can be implemented using network security groups or Azure firewalls to establish better infrastructure security.
- This IaC can be initiated via the following commands: "terraform init" "terraform plan -out main.tfplan" "terraform execute main.tfplan".
- Addition of more Terraform code is recommended to improve: more VMs/spokes and their scale sets should be added to effectively scale in and out depending on the workload, bastion or a strong implementation of SSH methods into the machines, etc.