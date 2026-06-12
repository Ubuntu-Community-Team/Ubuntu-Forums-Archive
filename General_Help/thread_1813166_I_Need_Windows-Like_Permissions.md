---
title: "I Need Windows-Like Permissions"
date: 2011-07-27
forum: General Help
---

### Post by jebbushell on 2011-07-27
It's like I moved into a house where I need to give my password when I want to go to the bathroom, and then again when I flush.

I have been through the sudo options, at least the elementary ones, and I currently have Ubuntu 11.04 but with Xfce and Thunar.  The Thunar is configured with a sudo action item.  

But it's still driving me mad!

I know what I'm doing.  I would like the file manager and the editor to do exactly what I say.  If I break something I promise not to cry.

Is there a chmod 777 style solution?  How about a Windows-like permissions option?  (A read-only setting is handy for check-outs.)   I'm sure I'm not the first Windows guy to blow a gasket about this.

Jeb ](*,)

---

### Post by aeiah on 2011-07-27
have a look here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

what are you trying to do that's causing you problems though? are you having to use sudo even for non-system files (ie, an external drive with the wrong permissions etc)?

---

### Post by jebbushell on 2011-07-27
Thanks for getting back so quickly.  

What I need is a Windows-like regime I suppose.  I am somewhat intimidated by the docs on rootsudo, and at the same time they seem wildly exaggerated.  What I want is Windows admin privileges or similar, because I'm a pro and I don't make many file management mistakes, and when I do I eat them.

Is there a hazard in rootsudo that might surprise a windows veteran? In other words, is it more dangerous than admin privilege in Windows?

---

### Post by bodhi.zazen on 2011-07-27
> **jebbushell said:**
> It's like I moved into a house where I need to give my password when I want to go to the bathroom, and then again when I flush.

I have been through the sudo options, at least the elementary ones, and I currently have Ubuntu 11.04 but with Xfce and Thunar.  The Thunar is configured with a sudo action item.  

But it's still driving me mad!

I know what I'm doing.  I would like the file manager and the editor to do exactly what I say.  If I break something I promise not to cry.

Is there a chmod 777 style solution?  How about a Windows-like permissions option?  (A read-only setting is handy for check-outs.)   I'm sure I'm not the first Windows guy to blow a gasket about this.

Jeb ](*,)

Sorry, this is not windows and chmod 777 will break your system.

You will need to learn to use sudo and gksu

gksu is for graphical applications such as nautilus and gedit.

The rootsudo link you were given explains the various options.

The permissions you are complaining about are the first line of defense against malware and crackers.

See also:

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

