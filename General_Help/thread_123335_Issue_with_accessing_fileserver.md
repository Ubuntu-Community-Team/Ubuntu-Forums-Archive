---
title: "Issue with accessing fileserver"
date: 2006-01-29
forum: General Help
---

### Post by associates on 2006-01-29
Hi,

I'm quite new to any linux system. Recently, i have installed linux ubuntu onto my laptop that's also got windows XP on it. I have a small network in the office i work. Most of them run on XP Pro. They all shared files very happily. I have a computer called fileserver dedicated to storing files.

I could access to the fileserver while running ubuntu on my laptop. I could browse all the other shared files on the fileserver as if i was on XP machine. 

My question is say i open up an excel file from the fileserver with openOffice.calc and like to save it as something else and put it into the fileserver. Am i allowed to do that? because by default it points to /home/myuser/. How do i go to other computers in the network and save it there?

Thank you very much in advance

---

### Post by dickohead on 2006-01-29
Since you are a new linux user i'm betting you don't understand a whole lot about Samba(SMB), so let me clear some things up:

File sharing between Linux and Windows is done via the SMB protocl (Samba), it allows both Linux and Windows machines access to a central file location, whether those files be on a Windows or Linux system.

You have a Windows fileserver yes? So what you need to do, is "mount" the remote samba share (windows share) to a folder on your system, ie:

\\fileserver\documents will be mapped to /home/user/network_docs (for example)
while \\fileserver may work in widnows, it most likely won't with Linux so instead use the IP address of the machine. Once it is mounted to a folder the contents of the remote share will appear as though they are stored locally on your machine, but they are not, any changes you make to files in that folder will affect the files on the server.

To mount samba shares you will use something like this:
mount -t smbfs \\192.168.1.1\documents /home/user/network_docs -a username=fred,password=freds_password

or you can use the smbmount command, but i'm not sure how it works at the moment.

---

### Post by associates on 2006-01-29
Thanks Dickohead for your reply.

Yes, I understand it now. So i believe that linux ubuntu must have had samba in it because i could just easily view my other files on other computers in the network by going to network server.

Sorry, may i ask again if you don't mind. Where should i put the following line into? I mean on windows, we can go to command prompt and type it in there. but what about linux ubuntu?.

I tried it by going to applications -> accessories -> terminal and typed in the one you told me to and it said that only root can mount. Then i changed directory to root such as myuser@ubuntu:/root$ mount -t smbfs \\192.168.1.1\documents /home/user/network_docs -a username=fred,password=freds_password

It said "mount: only root can do that". What's that mean?

Thank you in advance

---

### Post by nascent16 on 2006-01-29
In linux, most admin programs need to be run by 'root', the almighty owner of the desktop. This prevents you from accidentally executing things that you shouldn't. To execute a command as root, you just put 'sudo' in front of it:

sudo mount -t smbfs \\192.168.1.1\documents /home/user/network_docs -a username=fred,password=freds_password

You'll be asked for a password, just put your user password in again and it should work. You may also want to check out [www.ubuntuguide.org](www.ubuntuguide.org) for answers to this question and others that you might have at the beginning.

---

### Post by associates on 2006-01-30
Yup, I'll do that. Thanks a lot, Nascent16.

---

### Post by associates on 2006-01-31
Thank you Nascent16,

I have a situation here. I think i have forgotten the password for root.

Is there any way i can reset this? I'd never use linux before and didn't know that the root can be very powerful in the linux world.

Thanks heaps in advance

---

### Post by RAOF on 2006-02-01
[QUOTE=associates]Thank you Nascent16,

I have a situation here. I think i have forgotten the password for root.

Is there any way i can reset this? I'd never use linux before and didn't know that the root can be very powerful in the linux world.

Thanks heaps in advance[/QUOTE]
Unless you've specifically set it up, root doesn't have a password in Ubuntu.  When you use "sudo" to gain root privileges, you type your **own** password in.

---

