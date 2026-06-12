---
title: "Problem running program"
date: 2009-08-13
forum: General Help
---

### Post by Sander92 on 2009-08-13
Hey.
I'm a complete Ubuntu newbie, i havent used the OS for a long time but i managed installing some stuff. I've installed Nmap, which went fine by alittle help from google. But when I'm trying to hit "Scan" an error which says this pops up:
```

Error executing command

[Errno 2] No such file of directory

This means that the nmap executable was not found in your system PATH, which is

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
```I did some google searching, i came to a site which said this:

```
*>  /usr/local/bin is not in the default PATH. As mentioned above, currently *
*>  you have to install Nmap separately. When Nmap is compiled from source, *
*>  by default it is installed in /usr/local/bin. But /usr/local/bin is *
*>  *not* in the default OS X PATH! You will see an error in Zenmap: *
*>  "[Errno 2] No such file or directory". I don't recommend installing Nmap *
*>  with a prefix of /usr, but you can make a symbolic link from *
*>  /usr/bin/nmap to /usr/local/bin/nmap and it will work fine. *
```It tells me to make a symbolic link, but how do i do this?

Help appreciated, sorry for beeing a newb hehe

---

### Post by nikhilk on 2009-08-13
> **Sander92 said:**
> Help appreciated, sorry for beeing a newb hehe

Hey, everyone was a green user at some point, so no need to apologize at all!

First confirm that the nmap binary is indeed located inside /usr/local/bin by running this command in a terminal
```
ls -l /usr/local/bin/nmap
```
Then to create a symbolic/soft link in /usr/bin to /usr/bin/local/nmap run
```
sudo ln -s /usr/bin/local/nmap /usr/bin/nmap
```

But I would suggest that do not compile softwares from source unless it is the last resort. Ubuntu has a great package management system which makes the chore of maintaining softwares very easy. See [this]("https://help.ubuntu.com/community/SynapticHowto") link for details on Ubuntu's package management.

---

### Post by Sander92 on 2009-08-13
I ran the first command, the outcome was

```
ls: cannot access /usr/local/bin/nmap: No such file or directory
```

---

### Post by Sander92 on 2009-08-13
Sorry, found that the program was called zenmap, as nmap was a command line program and i chose the gui program.

Ran
```
ls -l /usr/local/bin/zenmap
```with the outcome

```
-rwxr-xr-x 1 root root 3571 2009-07-06 09:44 /usr/local/bin/zenmap
```Then i wrote

```
ln -s /usr/bin/local/zenmap /usr/bin/zenmap
```which gave

```
ln: creating symbolic link `/usr/bin/zenmap': File exists
```Then i ran the program, i still get the same error.

---

### Post by nikhilk on 2009-08-13
> **Sander92 said:**
> I ran the first command, the outcome was

```
ls: cannot access /usr/local/bin/nmap: No such file or directory
```

I forgot to mention that the ln command needs to be run using sudo, like this:
```
sudo ln -s /usr/bin/local/nmap /usr/bin/nmap
```
OK, so the nmap binary is not present in /usr/local/bin. Probably it is installed somewhere else or not installed in /usr/local at all.

At this point I suggest installing nmap from Synaptic. Is there any specific reason that you decided to compile from source as opposed to installing from Synaptic?

If you still want to use the compiled version could you specify the steps that you followed to compile and install nmap from source?

---

### Post by Sander92 on 2009-08-13
The file i downloaded had a .RPM ending, and i couldnt find .deb one. I found a software called alien to convert it to .deb.

Also i dont know what synaptic is...

---

### Post by nikhilk on 2009-08-13
> **Sander92 said:**
> The file i downloaded had a .RPM ending, and i couldnt find .deb one. I found a software called alien to convert it to .deb.

Also i dont know what synaptic is...

OK, just take a good look at the link I mentioned for Synaptic. Familiarizing yourself with Synaptic will go a long way.

You will need to add the Universe repository for installing zenmap from Synaptic. [Here]("https://help.ubuntu.com/community/Repositories/Ubuntu") is the link on Synaptic repository management.

---

### Post by Sander92 on 2009-08-13
I enabled universe thing, and i found zenmap, its working but its a quite old version. Is there a way to find updated versions on synaptic?

---

### Post by nikhilk on 2009-08-13
> **Sander92 said:**
> I enabled universe thing, and i found zenmap, its working but its a quite old version. Is there a way to find updated versions on synaptic?

Unfortunately, more often than not, you only have one version available when installing from Synaptic. I am afraid you won't find a newer version on Synaptic.

If you really need some of the features which are present only the latest version, you have to compile from source (your original approach).
Let me know if you cannot live with the older version and need to install the latest one.

---

### Post by Sander92 on 2009-08-13
I can use this one, would be nice to learn how to compile from source though, for later use ^^

Thanks alot for all the help :)

---

### Post by nikhilk on 2009-08-13
> **Sander92 said:**
> I can use this one, would be nice to learn how to compile from source though, for later use ^^

Thanks alot for all the help :)

Yes, sure. It is usually very simple with typically only 3 steps involved. See [this]("http://www.tuxfiles.org/linuxhelp/softinstall.html") simple and concise explanation of the same.

You are most welcome!

---

