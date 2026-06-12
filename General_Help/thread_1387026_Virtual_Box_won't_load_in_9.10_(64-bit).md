---
title: "Virtual Box won't load in 9.10 (64-bit)"
date: 2010-01-21
forum: General Help
---

### Post by AmpersUK on 2010-01-21
My computer crashed in the middle of loading up VirtualBox 64-bit.

Now whenever I try to load it I get the following error message.[INDENT][B]Only one software management tool is
allowed to run at the same time[/B]

Please close the other application e.g. 'Update
Manager', 'Aptitude' or 'Synaptic' first.

[/INDENT]I have no other programs open, and I get this error message even immediately I try to reinstall after a reboot.

Ampers

---

### Post by stim on 2010-01-21
try ```
sudo dpkg --configure -a
``` in a terminal. sounds like some stuff got mucked up.  

As a side note: all of your virtualbox configuration and data is in ~/.VirtualBox.  Should the above command not solve the problem, make a backup of ~/.Virtualbox, and uninstall/reinstall using the .deb from [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

---

### Post by AmpersUK on 2010-01-21
The sudo command didn't do anything, and  I cannot even download software from the Ubuntu Software centre without getting the warning: "Waiting for other software managers to quit" I might have to zap my computer and reload everything again. Rather a drastic move I know.

---

### Post by stim on 2010-01-21
That REALLY shouldnt be necessary, and is quite a pain.  

try this: [http://ubuntuforums.org/showpost.php?p=4137787&postcount=19]("http://ubuntuforums.org/showpost.php?p=4137787&postcount=19")

with the virtualbox package obviously instead of the cdemu package.  

best of luck!


this command
```
sudo fuser -v /var/lib/dpkg/lock
```

will tell you what process is locking the directory. you can then uninstall the offending package with the command from the post above

---

### Post by AmpersUK on 2010-01-21
> **stim said:**
> this command
```
sudo fuser -v /var/lib/dpkg/lock
```

I get:

ampers@ampers-desktop:~$ sudo fuser -v /var/lib/dpkg/lock
                     USER PID ACCESS COMMAND
/var/lib/dpkg/lock:  root       2860 f.... dpkg
ampers@ampers-desktop:~$

---

### Post by stim on 2010-01-21
fair enough, we certainly dont want to uninstall dpkg.  so, given this new information. lets try the following

first, kill the offensive dpkg process 
```
sudo kill -9 2860
```

then, you should be able to do updates, etc etc....if VirtualBox still wont load, then, uninstall virtualbox (!!!MAKE A BACKUP OF ~/.VirtualBox!!!, you can cp -r the directory, or just rename it to be something else so it does not get deleted during uninstall)

```
sudo dpkg --purge --force-remove-reinstreq --force-hold virtualbox-3.0
```

then, install vbox from the .deb provided by sun. I reccomend using this over the package provided in the repos

[http://download.virtualbox.org/virtualbox/3.1.2/virtualbox-3.1_3.1.2-56127_Ubuntu_karmic_amd64.deb](http://download.virtualbox.org/virtualbox/3.1.2/virtualbox-3.1_3.1.2-56127_Ubuntu_karmic_amd64.deb)


and then, of course, you will want to move your backed up copy of ~/.VirtualBox back into its original home, and BAM you will have all of your stuff back.

---

### Post by AmpersUK on 2010-01-22
Thanks for all your help, but in the end I decided to zap everything and start again.

But I found what was also a problem so I thought I'd share it with you all as you have been so helpful.

As I mentioned this was a new computer (64-bit) and a totally new installation.

So I loaded up again and had further issues with VBox (the full one from Sun) and had a little think abaout it and decided that the reason was probably because I had not run software update first - there were 199 updates.

So I loaded up 9.10 once more but this time I did a complete software update and loaded up the 199 updates before I loaded VBox.

And, guess what, some of the updates were for dpkg.

Everything is working well but you cannot load vbox before doing the updates.

Ampers.

---

### Post by c0mput3r_n3rD on 2010-01-22
Good rule of thumb is to always update before installing anythin... had to find out the hard way unfortunately :(

---

### Post by JiuJitsu500 on 2010-01-22
So did I, twice... and I feel you on that one :)

My stupid friend punched his computer because he didn't and managed to screw his hard drive.... no another good rule of thumb is never to punch your laptop :D I got it going again though once removing the hard drvie and letting him boot from a live CD every time for being an idiot :) lol felt like this story would make anyone feel a little less bad about anything they did to feel stupid :) works for me all the time...

---

### Post by c0mput3r_n3rD on 2010-01-22
> **JiuJitsu500 said:**
> So did I, twice... and I feel you on that one :)

My stupid friend punched his computer because he didn't and managed to screw his hard drive.... no another good rule of thumb is never to punch your laptop :D I got it going again though once removing the hard drvie and letting him boot from a live CD every time for being an idiot :) lol felt like this story would make anyone feel a little less bad about anything they did to feel stupid :) works for me all the time...


lol that's pretty funny.

---

