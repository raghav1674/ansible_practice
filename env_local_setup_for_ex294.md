## launch five vms( one gui and other four cli)

  1. one cli vm for controller node
  2. one gui vm for login to controller node
  3. three cli vm for managed node

## create devops user in Controller node as well as in the Managed node.
 
 '''>> useradd devops
 >> passwd devops
 enter the passwd '''

## grant sudo powers to devops user in Controller as well as the managed nodes.

'''>> vim /etc/sudoers.d/devops

devops ALL=(ALL)  NOPASSWD: ALL'''

## then in /etc/hosts in Controller Node

'''ip of managed node 1   servera.lab.example.com
ip of managed node 2   serverb.lab.example.com
ip of managed node 3   serverc.lab.example.com'''

also check the connectivity.

## change the hostname 

'''1. in Controller Node

>> hostnamectl set-hostname workstation.lab.example.com 
>> bash

2. in managed node 1

>> hostnamectl set-hostname servera.lab.example.com 
>> bash

3. in managed node 2

>> hostnamectl set-hostname serverb.lab.example.com 
>> bash

4. in managed node 3

>> hostnamectl set-hostname serverc.lab.example.com 
>> bash'''

## then login as devops user in Controller Node

'''>> ssh-keygen

press enter multiple times

then copy this key to the managed nodes

>> ssh-copy-id devops@servera.lab.example.com 
>> yes
>> type the passwd for the devops user u have set in that managed node 1

>> ssh-copy-id devops@serverb.lab.example.com 
>> yes
>> type the passwd for the devops user u have set in that managed node 2

>> ssh-copy-id devops@serverc.lab.example.com 
>> yes
>> type the passwd for the devops user u have set in that managed node 3'''


## In Gui vm

'''>> vim /etc/hosts

ip of controller node   workstation.lab.example.com'''


## Login from Gui vm to controller node

'''>> ssh devops@workstation.lab.example.com

>> yes
>> type the password for devops user u have set in Controller Node'''


##  Create a directory playbooks in /home/devops  in Controller Node after login.

 the path would be /home/devops/playbooks/



## install ansible using pip3 

>> pip3 install ansible  in controller node 

## inside playbooks/ 

create ansible.cfg and inventory file.

