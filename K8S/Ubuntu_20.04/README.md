[K8S Install by Ansible ]

* OS  Ubuntu 20.04 (GCP) 

* CNI Plugin : Flannel

* pod cidr : 10.244.0.0/16 ( Flannel Recommanded )
	- need to check /run/flannel/subnet.env

* Dashboard : 
	- version : 2.0
	- NodePort : 30001
	- Username : Admin

* Default SETING
	- SELINUX OFF
	- FIREWALLD OFF
	- SWAP OFF
	- /proc/sys/net/bridge/bridge-nf-call-iptables => 1
	- /proc/sys/net/ipv4/ip_forward => 1


* Necessary Packages
	- git
	- curl
	- wget
	- ansible

* Prepare 
	1. SSH check ( ssh-keygen > ssh-copy-id or copy public key to .ssh/authorized_keys )
	
	2. /etc/ansible/hosts setting
		- [k8s] : master & worker nodes ip
		- [master] : master node ip
		- [worker] : worker node ip
	
	3. Ansible work check > ansible all -m ping 

* Playbook order
	1. k8sinstall.yaml
	2. k8sset.yaml
	3. testfiles/test.yaml
	4. k8s_dashboard.sh

* log 
	- kubeadm init log 
 	- logfile name : k8s_token_[date]
