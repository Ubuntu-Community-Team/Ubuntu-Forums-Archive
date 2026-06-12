---
title: "No permission to move a file"
date: 2009-10-30
forum: General Help
---

### Post by stef25 on 2009-10-30
I created a file on my desktop and would like to copy it to etc/init.d. When I do so - "unable to move, no permissions".

How can I get the permissions I require?

---

### Post by Roasted on 2009-10-30
/etc/init.d is not wide open, it is a locked down system folder which requires root permissions to run.

You want to go to terminal and utilize the sudo mv command.

sudo mv /home/yourusername/Desktop/nameoffile /etc/init.d/

---

### Post by lavinog on 2009-10-30
is the file a script? are you familiar with scripting? moving a script to /etc/init.d will cause the script to be ran as root, and can break your system.

with that being said:
```

gksudo nautilus

```
or the command line way:
```

sudo mv filename /etc/init.d/

```

---

### Post by stef25 on 2009-10-30
Thanks for the fast replies. I created a startup script, as instructed here: [http://www.norio.be/blog/2009/10/problems-eclipse-buttons-ubuntu-910](http://www.norio.be/blog/2009/10/problems-eclipse-buttons-ubuntu-910)

The reason for this is a bug in the Aptana IDE. I have the script on my desktop and thought it had to go in the etc/init.d folder - or can it stay on my desktop?

If so, how do I trigger it to run via the command line?

---

### Post by lavinog on 2009-10-30
> **stef25 said:**
> I have the script on my desktop and thought it had to go in the etc/init.d folder - or can it stay on my desktop?

If so, how do I trigger it to run via the command line?
/etc/init.d is not where you want to put this.

check your path statement:
```

 echo $PATH

```
you should see something like this:
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```
move the script to /usr/local/bin
```

sudo mv scriptfile /usr/local/bin/

```
Now chmod it to be executable
```

sudo chmod 755 /usr/local/bin/scriptfile

```

now you should be able to execute it by using just the scriptfile name

---

### Post by stef25 on 2009-10-30
Thanks so much for your time, really appreciate it.

stef@stef-laptop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
stef@stef-laptop:~$ sudo mv scriptfile usr/local/bin/
mv: cannot stat `scriptfile': No such file or directory
stef@stef-laptop:~$ sudo mv scriptfile /usr/local/bin/
mv: cannot stat `scriptfile': No such file or directory
stef@stef-laptop:~$

Maybe there is a typo but I don't see it.

---

### Post by lavinog on 2009-10-30
replace "scriptfile" with the actual filename of your script

---

### Post by stef25 on 2009-10-30
d'oh sorry

stef@stef-laptop:~$ sudo mv home/stef/Desktop/start_aptana_sk  /usr/local/bin/mv: cannot stat `home/stef/Desktop/start_aptana_sk': No such file or director

Is it possible that the file is there but I still get this error? Right click properties says that it's a shell script so there is no file extension, correct?

---

### Post by lavinog on 2009-10-30
take advantage of tab completion when you can.
It looks like you are missing the leading /
it should be:
```
sudo mv /home/stef/Desktop/start_aptana_sk /usr/local/bin/mv
```

---

### Post by girto on 2009-10-30
What is the output of:
ls -la /home/stef/Desktop

Linux is case sensitive

---

### Post by stef25 on 2009-10-30
stef@stef-laptop:~$ sudo mv /home/stef/Desktop/start_aptana_sk  /usr/local/bin/
stef@stef-laptop:~$ sudo chmod 755 /usr/local/bin/start_aptana_sk
stef@stef-laptop:~$ 

So all good, thanks!

---

