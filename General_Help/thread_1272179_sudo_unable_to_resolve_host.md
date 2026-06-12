---
title: "sudo unable to resolve host"
date: 2009-09-21
forum: General Help
---

### Post by Inetrix on 2009-09-21
I installed Ubuntu today for the first time and I have tried to install a theme using this command:

sudo cp -r $HOME/Desktop/SlicknesS-black /usr/share/themes

whenever I enter it it says it is unable to resolve host.
How do I fix this problem? Thanks in advance!

---

### Post by mac9416 on 2009-09-21
Could you please copy/paste the output?

---

### Post by JC Cheloven on 2009-09-21
The most obvious possibility is that you don't actually have the file (SlicknesS-black) you're trying to copy in the directory you specified (your Desktop). 
Are you sure it is there?

---

### Post by Inetrix on 2009-09-21
I have both the actual file and the archive it was extracted from on my desktop.

output is:
patrick@patrix computer:~$ sudo cp -r $HOME/Desktop/SlicknesS-black /usr/share/themes
sudo: unable to resolve host patrix computer

it then prompts me for a password BUT for some reason I am unable to type in the console after the initial command was entered.

---

### Post by lisati on 2009-09-21
> **Inetrix said:**
> I have both the actual file and the archive it was extracted from on my desktop.

output is:
patrick@patrix computer:~$ sudo cp -r $HOME/Desktop/SlicknesS-black /usr/share/themes
sudo: unable to resolve host patrix computer

it then prompts me for a password BUT for some reason I am unable to type in the console after the initial command was entered.

I'm not sure about the "unable to resolve host" bit but it is normal for you to be asked for a password you're using sudo. Don't worry if it doesn't show as you type, this is a security precaution.

---

### Post by Inetrix on 2009-09-21
Ok now the password prompt is gone; unfortunately I am still having the same problem with the 'unable to resolve host' error.

---

### Post by mac9416 on 2009-09-21
Could you please post the contents of your /etc/hosts file?
And your /etc/hostname if you would.

---

### Post by Inetrix on 2009-09-21
127.0.0.1 localhost
127.0.1.1 patrix computer
::1       localhostip6-localhost ip6-loopback
fe00::0   ip6-localnet
ff00::0   ip6-mcastprefix
ff02::1   ip6-allnodes
ff02::1   ip6-allrouters
ff02::3   ip6-allhosts

when I tried to type the file directory in my console it said: bash: /etc/hosts: Permission denied
hostname: **'patrix computer'**

---

### Post by Inetrix on 2009-09-21
Reading around this seems to be a quite common problem. I attempted to fix it by using a common method I've seen it brings me a new error:
patrick@patrix-computer:~$ gksu gedit /etc/hosts

> (gksu:9847): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
No protocol specified
(gedit:9848): Gtk-WARNING **: cannot open display: :0.0
patrick@patrix-computer:~$ gksu gedit /etc/hosts

---

### Post by mcduck on 2009-09-22
Are you trying to run this command (the one you mentioned in your post):
```
sudo cp -r $HOME/Desktop/SlicknesS-black /usr/share/themes
```
..or this one:
```
sudo cp -R $HOME/Desktop/SlicknesS-black /usr/share/themes
```

If the first one, there's your problem. The option for recursive copy is "-R", not "-r".

What comes to the last error related to Gedit, did you try running that in a terminal emulator (such as Gnome-terminal), or in a TTY?

---

### Post by JC Cheloven on 2009-09-22
> **Inetrix said:**
> I have both the actual file and the archive it was extracted from on my desktop.

output is:
patrick@patrix computer:~$ sudo cp -r $HOME/Desktop/SlicknesS-black /usr/share/themes
sudo: unable to resolve host patrix computer

it then prompts me for a password BUT for some reason I am unable to type in the console after the initial command was entered.

First: there could be a problem with the name of your computer: it's a bad idea to choose one with spaces inside. I guess from your later post that you fixed it already (?)

Second: The recursive -R has to be capital, as mcduck said

Third: You're only trying to copy files. Why don't open nautilus with root privileges and copy comfortably using the gui? (from terminal "gksudo nautilus")

Don't dispair, you're only facing tiny newcomer problems. You'll get used soon to the way basic things should be done, and you'll feel comfortable.
Greetings

---

### Post by mac9416 on 2009-09-22
Actually, I looked at the cp man page, and it chows that either -R or -r can be used.

OK, Inetrix, here's what I've learned from a little Googleing. Sudo uses the 127.0.1.1 line in you /etc/hosts file, and if it's wrong you can't use sudo. Unfortunately, you have to use sudo to edit /etc/hosts. So, you must boot into recovery mode, then run sudo nano /etc/hostname. Change the file to look like this:
> [COLOR="Red"]patrix-computer[/COLOR]
Then run sudo nano /etc/hosts and edit it to look like this:
> 127.0.0.1 localhost
127.0.1.1 [COLOR="red"]patrix-computer[/COLOR]
::1 localhostip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::1 ip6-allrouters
ff02::3 ip6-allhosts

Than boot back into normal mode. sudo should now work fine.

I should to try and install Ubuntu with a space in the hostname and see if it breaks sudo. If so, that's probably a bug in the installer.

---

### Post by 3rdalbum on 2009-09-22
mac9416: second command should be:

```
sudo nano /etc/hosts
```

Thanks for telling me about this anyway, now I know what to do if anyone asks me how to change their hostname without breaking sudo!

---

### Post by mac9416 on 2009-09-22
Thanks for pointing that out, 3rdalum. Still kinda early where I am. ;-)

---

