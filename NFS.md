## Part 1 - NFS Server Configuration ( / 6)

1. Configure a space, use the `ext4` filesystem
    - Document the commands used and what they do
2. `mount` the partition to a folder on your AWS instance.  Allow `other`s to add files / folder and edit files / folders within the folder.
    - Document the commands used and what they do
3. Configure `/etc/fstab` to auto mount the partition to the folder on boot.
    - Line added to `/etc/fstab`
    - Command to test `/etc/fstab`
3. Install `nfs` server 
    - Command to install
     -sudo yum -y install nfs-utils
    - Command to check service status
     - sudo service nfs status
4. Configure `/etc/exports` to share folder
    - Line added to `/etc/exports`
    - Describe the options you used in exports and why.  If you used no options, describe all default options that would apply.
5. Enable your `nfs` share
    - Command to export all directories in `/etc/exports`
      -exportfs -r 
    - Command to restart `nfs`
      -Sudo service nfs restart

Screenshot your block devices (`lsblk`), the permissions of your shareable folder, and what folders are currently shared (`exportfs`)
![image](https://user-images.githubusercontent.com/112041435/224788876-509c7b90-bfec-4a4e-a8a1-b18780df5365.png)
![image](https://user-images.githubusercontent.com/112041435/224788928-061c25c0-d2c7-4398-a01d-9b55e22460f0.png)

## Part 2 - Firewall Fixes ( / 5)

Screenshot of updated Inbound rules and included with documentation ( / 1)

Inbound rules: ( / 4)
- ALLOW `https` from any IPv4 address (can add IPv6)
- ALLOW `http` from any IPv4 address (can add IPv6)
- ALLOW `ssh` from "home" - public IP from ISP
- ALLOW `ssh` from WSU - 130.108.0.0/16
- ALLOW `ssh` within virtual network - 10.0.0.0/16
- ALLOW `nfs` from "home" - public IP from ISP
- ALLOW `nfs` from WSU - 130.108.0.0/16
- ALLOW `nfs` within virtual network - 10.0.0.0/16

![image](https://user-images.githubusercontent.com/112041435/224790401-f8c633ab-0818-4fe6-9575-52884da4c33b.png)



## Part 3 - Mounting an NFS Share ( / 6)

1. Install NFS client
2. Create a directory to mount the NFS share to
   - EFS-mount-Point
4. Mount the share folder using the host's IP (public or private)
5. Prove that you can add files to the `nfs` share
  -touch test-file.txt
6. Document how to `unmount` the `nfs` share
   
Screenshot what is currently mounted by `nfs` clients using `nfsstat` and included with documentation.


![image](https://user-images.githubusercontent.com/112041435/224793656-df0c200a-ff8c-4275-9703-c00546bd928f.png)




