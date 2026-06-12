---
title: "Windows 7/Samba"
date: 2009-11-12
forum: General Help
---

### Post by jared.j on 2009-11-12
I am having issues with both of my Windows 7 machines being able to access my Samba shares on my Ubuntu Server.

I can see the server in the Network and Sharing center on both Windows 7 machines but when I click it I get the message Windows cannot access //Servername.

I have heard that the is extra steps that need to be done in Windows 7 to get this to work but have been able to find what those are or even confirm this.

Can anyone help me get this resolved and working?

---

### Post by Giblet5 on 2009-11-12
Is Windows 7 configured for a domain, or for a workgroup?

(Click the menu icon, right-click "Computer" and select "Properties...")

Click the "Computer Name..." button.


I make my Win7, Vista, and XP installs part of the "PHRENZY" workgroup, and my /etc/samba/smb.conf includes the line (within the Global section):
```
workgroup   = PHRENZY
```

Then I restart samba via ```
sudo /etc/init.d/samba restart
```

It's very smooth sailing from there.

---

### Post by jared.j on 2009-11-12
It is configured as a workgroup.

---

### Post by Giblet5 on 2009-11-12
Did you fix your smb.conf yet?

---

### Post by jared.j on 2009-11-12
yes I already had it set to the workgroup for the windows 7 machines.

---

### Post by Giblet5 on 2009-11-12
> **jared.j said:**
> yes I already had it set to the workgroup for the windows 7 machines.

Thanks for sharing that tidbit. :|

Try to keep in mind that nobody here will magically know what you have/haven't done to diagnose this issue: we're clever, not clairvoyant...

Have a good day.

---

### Post by jared.j on 2009-11-12
ok I still have the problem thou.

Any ideas on how to fix it?

---

### Post by VastOne on 2009-11-12
I am having this same issue.  In Windows 7 I have stayed with the default of WORKGROUP which is what is there by default in smb.conf

I am able to ping the Ubuntu Server but cannot browse it at all.

---

### Post by evilbuntu on 2009-11-24
are you using webmin?

i myself have been having samba issues right now but its more on the windows end.

i can see the other PCs in the WG but it wont mount them from ubuntu's explorer. I have to enter the smb://000.000.000.000 to get it to find.

then i dont have rights to put anything on teh windows machines.

---

### Post by VastOne on 2009-11-24
> **evilbuntu said:**
> are you using webmin?

i myself have been having samba issues right now but its more on the windows end.

i can see the other PCs in the WG but it wont mount them from ubuntu's explorer. I have to enter the smb://000.000.000.000 to get it to find.

then i dont have rights to put anything on teh windows machines.

I am not using webmin, never heard of it until this post.

I am still having issues with Samba on both sides not seeing and/or connecting correctly.  From Win 7 to Ubuntu Koala, I can only connect via mapping network drive and ip address to the shares and from Koala to Win 7 I cannot access or connect to the shares at all with the ubiquitous "Failed o retrieve share list from the server" message 

I have followed every thread here and googled to no avail.

---

### Post by stuart-b on 2009-11-24
I also have the same problem with Windows 7,

One thing I tried was changing Network settings to allow No Password Required for sharing, it seemed to work, but now always asks me for user/password, even though I have set it to not required...

---

### Post by VastOne on 2009-11-25
With the new kernel upgrade and other package upgrades, all my issues with Samba to W7 are now resolved, I can browse all the shares and have no errors.

From W7 to Ubuntu shares, I cannot (nor ever have) browse them or see them in the network, but I have always been been able to connect to them via IP address so it is a non issue.

I am now at Version 3.4.0 of Samba

---

### Post by Charlietje on 2009-11-25
Hi,

I have no problem accessing my smb shares from ubuntu on win7.

What have you done to make the share?
Did you try to map it?
Did you try to map it in commandline?
When you tried to map it, and it didn't work, did you check the var/log file to see why it was refused?

Whithout error messages or your steps, it's difficult to troubleshoot.

Please provide more info.

Regards

---

### Post by ve3dvv on 2009-11-25
- I had to set the server to have a fixed IP address.
- make sure the share is mounted (did not automount from fstab)
- manualy start samba 

John

---

### Post by Roasted on 2009-11-25
Let's see some more info here to the users with problematic Samba machines.

Post your entire smb.conf file.

What program did you use to configure Samba?
Do you have the "samba users" added as a local user on the Ubuntu "server" as well?
At any point in time was this Samba setup working and then magically stopped?
What are the permissions on the shares you're linking to on the Ubuntu machine? If you can navigate via terminal to the shares you're linking and run ls -l, that'd be great.

---

### Post by rldev on 2009-12-14
I can access win 7 from Ubuntu. Fron win 7, I can't see any ubuntu machines. I don't know where to begin.

---

### Post by VastOne on 2009-12-14
> **rldev said:**
> I can access win 7 from Ubuntu. Fron win 7, I can't see any ubuntu machines. I don't know where to begin.

browse by IP of the Ubuntu machine and that should give you a listing of the shares

---

