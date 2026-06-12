---
title: "Changed user to administrator but still have to give password"
date: 2012-05-11
forum: General Help
---

### Post by ltwinner on 2012-05-11
I am currently using Ubuntu in a virtual machine. I have no need for separation between administrator and regular user as I am the only person using my PC so I changed my user account type to Administrator. However I am still getting asked 'Enter your password to perform administrative tasks'. Anyone know why it is still asking me for the password and how to set it up so that it doesnt?

---

### Post by drmrgd on 2012-05-11
You might have a look at this [RootSudo Documentation]("https://help.ubuntu.com/community/RootSudo").  Being an administrator gives the user permission to use sudo to run administrative tasks.  Still, though, sudo is required in order perform any admin tasks, and administrator is not the same as root, which has ubiquitous authority to do anything on the system.

---

### Post by wilee-nilee on 2012-05-11
> **ltwinner said:**
> I am currently using Ubuntu in a virtual machine. I have no need for separation between administrator and regular user as I am the only person using my PC so I changed my user account type to Administrator. However I am still getting asked 'Enter your password to perform administrative tasks'. Anyone know why it is still asking me for the password and how to set it up so that it doesnt?

Ubuntu is designed to have superuser access with a password, if you run in root you will just have problems. You can setup a no password access though for super use but it is not advised.

Being the sole user is not a good explanation to remove password use to be honest. There is not one that is valid really.

If you want to run with no password get a distro that runs in root like puppy linux, it is designed to run that way.

---

### Post by ltwinner on 2012-05-16
> **wilee-nilee said:**
> Ubuntu is designed to have superuser access with a password, if you run in root you will just have problems. You can setup a no password access though for super use but it is not advised.

Being the sole user is not a good explanation to remove password use to be honest. There is not one that is valid really.


Eh, it's a very good reason to remove the password. It seems I have to type the password every 2 mins and for what reason exactly? I am the only person using this ubuntu, and the only person who every will use it. It is ridiculous having to type a password every 2 mins when you are running ubuntu on a VM and you are the only person using it. What benefit is the password process giving me? None.

---

### Post by lisati on 2012-05-16
> **ltwinner said:**
> What benefit is the password process giving me? None.
Yes, it makes sense that because you are the only user of a computer, you should be able to choose not to require a password for every administrative task.

On the other hand, many of us prefer the extra layer of security that a password provides. One example of when this would be useful is when we visit a website which causes a rogue script to open up in your browser: you don't want random web pages or rogue email attachments to do stuff to your system without your knowledge or permission.

---

### Post by Derek Karpinski on 2012-05-16
> **ltwinner said:**
> Eh, it's a very good reason to remove the password. It seems I have to type the password every 2 mins and for what reason exactly? I am the only person using this ubuntu, and the only person who every will use it. It is ridiculous having to type a password every 2 mins when you are running ubuntu on a VM and you are the only person using it. What benefit is the password process giving me? None.


Then log in as root, and have fun. Or run windows.  There is a reason an admin does not have the same privledges as root, and require a password.  This model has served Linux and Unix pretty well.  Look at windows security history.

How long does it take to type in your password?  Can't be more than 10 seconds.

---

### Post by BlinkinCat on 2012-05-16
> **ltwinner said:**
> It is ridiculous having to type a password every 2 mins when you are running ubuntu on a VM and you are the only person using it. What benefit is the password process giving me? None.

Every 2 minutes ? - ;)

---

### Post by oldos2er on 2012-05-17
> **ltwinner said:**
>  It seems I have to type the password every 2 mins and for what reason exactly? 

```
sudo -i
``` will give you a persistent root shell.

---

### Post by ltwinner on 2012-06-24
> **BlinkinCat said:**
> Every 2 minutes ? - ;)

Yes I do development work in lots of languages and in lots of different environments and I constantly have to install packages and perform other admin tasks.

> **Derek Karpinski said:**
> Then log in as root, and have fun. Or run windows.  There is a reason an admin does not have the same privledges as root, and require a password.  This model has served Linux and Unix pretty well.  Look at windows security history.

How long does it take to type in your password?  Can't be more than 10 seconds.

One of the major complaints about Vista was the hassle caused by its UAC and ubuntu is just as bad.

It is terrible work practise to have to type in unnecessary passwords every few minutes. There are many users who have situations where it is completely unnecessary to have password protection. Such as in my case where I am running several ubuntus on virtual box and I do not need password protection as there is NO security risk. Obviously passwords protection is a must for many users but its not for me, I am not suggesting that ubuntu should ditch the password system as you seem to imply I am suggesting. For the users who are running ubuntu in situations where passwords are not necessary it should be possible to disable them.

---

### Post by philinux on 2012-06-24
> **ltwinner said:**
> Eh, it's a very good reason to remove the password. It seems I have to type the password every 2 mins and for what reason exactly? I am the only person using this ubuntu, and the only person who every will use it. It is ridiculous having to type a password every 2 mins when you are running ubuntu on a VM and you are the only person using it. What benefit is the password process giving me? None.

You may have missed this link. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Scroll to bottom.

---

### Post by ltwinner on 2012-06-24
> **philinux said:**
> You may have missed this link. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Scroll to bottom.

ill give it a try...

---

### Post by oldos2er on 2012-06-24
> **ltwinner said:**
> It is terrible work practise to have to type in unnecessary passwords every few minutes. 

```
sudo -i
``` will give you a persistent root shell.

---

### Post by HiImTye on 2012-06-25
you should give something like Cygwin a try. I'm not really sure why you are using dedicated Linux (in a VM) in the first place as it seems contrary to your usage needs

---

### Post by MrZorg2012 on 2013-01-23
> **oldos2er said:**
> ```
sudo -i
``` will give you a persistent root shell.

That only works until you close terminal... next time, you have to do it again. 
My main issue with these forums, are that it always turns into a flamming war on how to do something. With smart A** responses. Which are less than helpful. I have even seen a reply with "use something like puppy linux which runs at root". Now I ask, if it's SO bad to run without the password, as puppy does?, then why would puppy put that out?
I also would LOVE to dump the password thing. Have my account to be an admin, but still it's asking. Done the visudo to add my account name and set it to show no password. But still it ask. Knoppix is also another version that does not require passwords. Are you saying puppy and knoppix will get your computer all crashed and/or screwed up?
I just want to mount my extra drive without a password. But the "tutorial" on fstab is total Greek, does not even tell you what file name it has to be ie: fstab.conf etc...
I would love to be able to run normal user, and have access to "open folder as root" without having to put in a password, and mount my NTFS without putting in the password. That would be enough for me. 
As far as hackers, I'm behind NAT, and the pc is mine and mine alone, no one gets on it but me. Also it's not a laptop I take with me, it's my home computer.
Been playing with Linux for years, just not totally technical, mainly to see what it's all about. I just wonder, if running in root shell is SO BAD, why do some distros let you do that, while some say "heck no techno"...

---

### Post by oldos2er on 2013-01-24
I see you've posted in a few threads. The best way to get answers to your questions is to start your own thread, and give as much detail as possible. [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

