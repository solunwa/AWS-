#AWS-
Attaching and mounting EBS/NFS/EFS volumes:
This gives information on the creation of ebs voln and mounting them on servers, it also shows how to connect multiple network file system (nfs) using efs
====================================
Your ebs volume created an the ec2 created must be in the same availbilty zone AZ
for you to be able to mount the ebs voln

[ec2-user@ip-10-0-0-23 ~]$ history
    1  exit
    2  clear
    3  df -h
    4  lsblk
    5  ls /
    6  clear
    7  lsblk
    8  df -h
    9  clear
   10  mkdir /app
   11  sudo mkdir /app
   12  clear
   
   13  lsblk  =    
   14  sudo file -s /dev/xvdf #(To check the status to know if the file is formated or not)

   15  sudo mkfs -t xfs /dev/xvdf  #(Make directory to create a file system)
   
   16  clear
   17  sudo mkdir /data    #(Create another mount point called data)
   18  la /app
   19  ls /app
   20  ls /data
   21  df -h

   22  sudo mount /dev/xvdf /data  #(mounting the created ebs volume on data directory)
   23  clear
   24  lsblk
   
   25  sudo mount /dev/xvdf /app   (mounting the created ebs volume on app directory)
   26  lsblk
   27  df -h
             reboot / 
             init 6  / 
             init 0 /  
   28  sudo cp /etc/fstab /etc/fstab.orig   #(This command is to save make the mounted ebs volume to stay after reboot ie to be permanent)
   29  history

Volume expansion - vertical   [4gb-->7gb] 
Volume expansion - horizontal [v1=8g, v2=7g, v3=6g]   

Traditional volume mgt and LVM use to require SystemsAdmin 
skills to perform. Today cloud computing skills are required

Lambda functions:
=================  
  If we have upto  75% volume usage increase vol by 20%   
 Note to enable your cross region when creating snapshot Life cycle management
 cross account 
    aws account1 = email/password 
       database servers  
    aws account2 = email/password   
      backup data in   

 cross region   

from a snapshot, we can create:
  Snapshots are stored in S3 and help in creating 
   1. volumes  
   2. images = AMI  :
        Community  
        marketplace  
        myAMI/GOLDEN AMI  
  DOCKER SERVER = 
    OS            = ubuntu  
    softwares     = docker, git, wget, java     
    applications  = myaapp 
    files       

  Jenkins SERVER = :
    OS            = ubuntu  
    softwares     = jenkins, git, wget, java     
    applications  = myaapp 
    files         =-   
    jobs          =  

File storage system : It is a network file system managed by AWS
efs volume = file storage:(Network file Systems)
remember that nfs port is : 2049
   Required mounting 
   sudo yum install nfs-utils
sudo mkdir efs       
sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-0506f72fa378122f3.efs.us-east-1.amazonaws.com:/ efs
