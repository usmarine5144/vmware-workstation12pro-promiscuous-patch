VMware Workstation 12 Pro promiscuous mode patch
================================================

This patch will create the necessary group and changes necessary
in order to enable promiscuous mode in vmware workstation 12.

The problem is that by defult the vmware service creates vmnet\*
devices that are only writable to by root. In order to put the 
device in to promiscuous mode the user starting the VM must be able
to write to the device. 

This patch will do the following
  - Create a group called vmnet.
  - Apply a patch to the vmware init script.
  - Restart the vmware service.

After this patch has been run you must add users in to the vmnet
group so that they are also provided the write ability to the device
  * adduser \<username\> vmnet
