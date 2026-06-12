---
title: "How can I mount shares from windows enviorment on ubuntu 11.04"
date: 2011-08-08
forum: General Help
---

### Post by nap1 on 2011-08-08
Hello, 

I have install ubuntu 11.04 and would like to know what is the best method of installing shares using active directory credentials. I have already installed centrifyexpress to use ad credentials for loging into ubuntu. But now would like to mount share using the same credentials that I used to login, however I do not feel confortable inputting my password in script file to mount the shares. So it can use the login credentials I used with centrify express then that would be great. 

All your help is greatly appreciated. 

Thanks

---

### Post by collisionystm on 2011-08-08
What I do is mount the share in linux using /etc/fstab

you create a credentials file in the /root folder. In here is where you put the username and password.

set the permissions so its only readable by root.

If this sounds interesting to you, I can give you a short tutorial how to do it. let me know

---

### Post by nap1 on 2011-08-11
Sure you can I can always use your method. Thanks! I eventually would like to find out if there is way to do this without password and just use the password from login. 

Has anyone ever used and installed pam_mount. It seems it might be possible with this?

Thanks

---

### Post by collisionystm on 2011-08-12
> Sure you can I can always use your method. Thanks! I eventually would like to find out if there is way to do this without password and just use the password from login. 

Has anyone ever used and installed pam_mount. It seems it might be possible with this?

Thanks

First

On your Ubuntu box you need to install samba and smbfs. I cant remember if they come packaged together, so try to install separately just in case.

```
sudo apt-get install samba
```
```
sudo apt-get install smbfs
```

On your Windows box you need to share the folder.
On my boxes I just used the administrative account for sharing, but you can create a separate account called Ubuntu or something for organizational purposes. Be sure to give the account admin privileges.

When you try to reach the Windows share from another computer, you should be prompted with a username and password prompt. If that happens, we are good.

NOW

On back to your Ubuntu box. You need to create a file to hold the Windows Credentials to access the share. 

```
sudo nano /root/.<servername>
```
I.E. sudo nano /root/.apollo

In the file you need to set it like this

username=server\administrator(or other)
password=********(your password)

i.e. 

> username=apollo\ubuntu
password=ilovelinux

CTRL+X to save

Make sure to chmod the file so no one else can access it. 

sudo chmod 700 .filename

now

Make the folder on your Ubuntu box that you want the Windows directory to mount at

You can do something like...

```
sudo mkdir /apollomount
```

Next

cd to that folder

```
cd /apollomount
```

```
mkdir C
``` ( for c drive ) or other share

Now you should have a folder for your server, and in that folder another folder to actually mount windows on.

```
sudo nano /etc/fstab
```

Add a line that looks just like this

> //172.16.66.137/C$ /apollomount/C cifs sec=ntlmv2,credentials=/root/.apollo,iocharset=utf8,file_mode=0777,dir_mode=0777 0

CTRL+X to save

Now to mount the drive

```
sudo mount -a
```

You should not see any feedback unless you have an error. To check your disk mount, issue the command

```
df

```


Now your Windows drive has been mounted on Ubuntu securely and it will mount on its own after every reboot.

If you ever need to un-mount the drive to edit your /etc/fstab issue the command

```
sudo umount -a
```

---

