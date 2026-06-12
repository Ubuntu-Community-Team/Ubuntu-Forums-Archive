---
title: "Block webpage in /etc/hosts?"
date: 2011-05-15
forum: General Help
---

### Post by autonym on 2011-05-15
Hi!
I'm using firefox and I'm trying to block google.com by ading the line *127.0.0.1 google.com* in /etc/hosts but it don't work. I get this error message in terminal;

```
(gedit:11640): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.ZTL1UV': No such file or directory

(gedit:11640): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```Any tips on what I'm doing wrong?

---

### Post by Dave_L on 2011-05-15
How exactly are you editing /etc/hosts? It's owned by root, so you need to use a command such as

```
sudo nano /etc/hosts
```

or

```
gksudo gedit /etc/hosts
```

---

### Post by dino99 on 2011-05-15
/etc/hosts works but its hard to maintain with long list, better to set your prefs with either:
- ufw (gufw)
- moblock or iplist or similar

---

### Post by autonym on 2011-05-16
> How exactly are you editing /etc/hosts?I'm using *sudo gedit /etc/hosts*. When I use *sudo nano /etc/hosts* I don't get any error messages in terminal but it still don't work.
> 
/etc/hosts works but its hard to maintain with long list, better to set your prefs with either:
- ufw (gufw)
- moblock or iplist or similar     I don't know how those ip filtering (blocking) programs works sadly. It wont be a long list to maintain in /etc/hosts though since it's only google.com I want to block...

---

### Post by Dave_L on 2011-05-16
> **autonym said:**
> I'm using *sudo gedit /etc/hosts*. When I use *sudo nano /etc/hosts* I don't get any error messages in terminal but it still don't work.

I'm able to edit the file successfully using both of those commands, so I don't know why it's not working for you.

---

### Post by autonym on 2011-05-16
> I'm able to edit the file successfully using both of those commands, so I don't know why it's not working for you.

Yes! At last! It's solved!!
It was a two step solution:

1: You'll have to write both google.com *and* **www.**google.com in /etc/hosts

2: You'll also have to restart firefox for this to work

Thanks for all the help and all the time! I'm glad this one got solved!

---

### Post by arvevans on 2011-05-16
Not sure I understand just what the OP wants to do, but google.com is not on 127.0.0.1 IP address.  That IP Address is the Linux internal loop-around and is used by several internal programs to test and to provide local services.  

If you are trying to block unsolicited incoming from Google, a generic firewall will do that.  If you want to block responses to your Google queries, that is another matter all together and will probably require that you get up to speed with using IP-Tables as a filter.

If the intent is just to block users from using Firefox, you can do that by removing the installed Firefox with the package manager.  Unlike Microsoft and it's browser, the Firefox browser is not deeply embedded inside Linux.

---

### Post by 5149.5 on 2011-05-16
> **arvevans said:**
> Not sure I understand just what the OP wants to do, but google.com is not on 127.0.0.1 IP address.  That IP Address is the Linux internal loop-around and is used by several internal programs to test and to provide local services.  


Apparently the OP doesn't want anyone using the computer to access google. Setting it's address to 127.0.01 in the hosts file will do that. This is a trick utilized by some "services" for blacklisting certain websites on windows machines.

---

