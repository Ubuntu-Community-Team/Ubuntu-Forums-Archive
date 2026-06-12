---
title: "How to redirect output of Xorg -configure to a file"
date: 2010-06-29
forum: General Help
---

### Post by gjbob on 2010-06-29
Ubuntu 10.04

I booted to command line only and entered the following command:
Sudo Xorg -configure > xorglog.txt

the command seems to run just fine and does create a new xorg.conf.new file but I would like to see all the output of the Xorg -configure command but it just scrolls by too fast and I can't go back to see it.  Hence this is why I'm trying to do the > .  It seems to ignore the >.  

Anybody have any ideas how I can see what the command is doing?

---

### Post by TeoBigusGeekus on 2010-06-29
```
sudo Xorg -configure | tee xorglog.txt
```

---

### Post by sisco311 on 2010-06-29
EDIT:
```
sudo Xorg -configure -logfile filename
```
The default logfile is /var/log/Xorg.n.log, where n is the display number of the Xorg server:
```
man Xorg | less +/-logfile
```




Or redirect the stderr to the file.

If your (normal/admin) user has write and execute permission for the directory where you want to save the log file, then run:
```
sudo Xorg -configure 2> xorglog.txt
```
to redirect strderr & stdout:
```
sudo Xorg -configure &> xorglog.txt
```


If you need root privileges to create the log file, then start a root shell:
```
sudo -i
Xorg -configure 2> xorglog.txt
#or
Xorg -configure &> xorglog.txt
exit
```

or use tee:
```
sudo Xorg -configure 2>&1 >&- | sudo tee xorg.log
sudo Xorg -configure 2>&1 | sudo tee xorg.log
```

But if you don't want to save the output to a file, you can simply pipe stderr to less:
```
sudo Xorg -configure 2>&1 >&-| less
```
or both stderr & stdout:
```

sudo Xorg -configure 2>&1 | less
sudo Xorg -configure |& less
```

Check out:
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html)
[http://tldp.org/LDP/abs/html/io-redirection.html](http://tldp.org/LDP/abs/html/io-redirection.html)
[uhelp]community/RootSudo#Downsides%20of%20using%20sudo[/uhelp]

---

### Post by gjbob on 2010-06-30
TeoBigusGeekus
sudo Xorg -configure | tee xorglog.txt did not work.  It created both the log file and the xorg.conf.new so it ran just fine but the xorglog.txt file was empty.

---

### Post by gjbob on 2010-06-30
Sisco311:  These commands worked fine.  The command 
sudo Xorg -configure -logfile filename
had more content in the logfile.  Thank you very much for your help

---

