---
title: "Display a message everytime I turn off"
date: 2009-08-20
forum: General Help
---

### Post by madu on 2009-08-20
Hello guys,

I want to have a message displayed to me everytime I turn off the machine. There are couple of chores that I need to before I leave and I forget them most time. What is the easiest way to accomplish this?

Cheers.

---

### Post by tgeer43 on 2009-08-20
Not a definitive answer but here's a good start:

When you select shutdown, all scripts in /etc/rc0.d are run. Actually they are symbolic links to scripts in /etc/init.d. Basically you place your script in /etc/init.d and run 'update-rc.d' to create the links for you. There are certain naming conventions and other considerations. See the readme files in /etc/rc0.d and etc/init.d for more details.

tgeer

---

### Post by pmlxuser on 2009-08-20
creat a script that does that list and let the commputer shutdown on itself. 

by the way
"you cant have messages displayed when the machine is off how ever you can ahve messages displayed if you initiate a shutdown."

---

### Post by madu on 2009-08-20
Thanks guys.

Actually these are not system related stuff. :)
I need to do some other things like pick some print outs, take the USB disk, etc., before I leave for home. So what I want is the system to display this list when I hit shut down. 

Because no matter how much remember these, when I am about to leave I always forget one or two.

So it is not a script that I want to run, per se. but rather to display a list of to-do's.

Cheers.

---

### Post by tgeer43 on 2009-08-20
> **pmlxuser said:**
> creat a script that does that list and let the commputer shutdown on itself. 

by the way
"you cant have messages displayed when the machine is off how ever you can ahve messages displayed if you initiate a shutdown."
WTF???

I realize that you are from Central Africa and that English is not your native tongue but that would not make a bit of sense in any language. Hehe...

---

### Post by MaxIBoy on 2009-08-20
Create an initscript which will display your list and then ask you to hit enter before it will shut down properly. 

Make the script in /etc/init.d and give it the name reminder.sh.

Copy this into it. 
```
#! /bin/bash
echo "Hello, you seem to be shutting down. Remember to do the following:
1. Print stuff out.
2. Make sure cake is in fridge.
3. Don't forget flash drives.
4. Whatever else it is you need to do.
5. Edit this file to suit your needs.

Hit enter to continue shutting down."
read
```

Run the command "sudo chmod +x /etc/init.d/reminder.sh" to allow the program to run as a program.


Next, make a shortcut to the file and move the shortcut to /etc/rc0.d

You should edit the name of the shortcut. Add an uppercase "S" to the beginning of it, and after the S add a two-digit number. Try to get it to run before halt by giving it a smaller number, so if halt is called "S90halt," name the shortcut to your new initscript "S89reminder.sh." That way it will run just before the computer actually turns off. 

I already explained initscripts earlier today, see my other post here: [http://ubuntuforums.org/showpost.php?p=7813454&postcount=5](http://ubuntuforums.org/showpost.php?p=7813454&postcount=5)

---

### Post by madu on 2009-08-20
Thats soo thorough MaxIBoy.
Thanks heaps. I need to re-read it again and will try to do it and get back.
Cheer.s!

---

### Post by madu on 2009-08-20
Hi MaxIBoy.

I just tried out what you described and it didn't work the first time. I am little unclear as how to create a shortcut. I created a symbolic link. Would that be ok?

Cheers.

---

### Post by tgeer43 on 2009-08-20
A symbolic link is the same thing as a shortcut so you're fine and you don't even have to create it yourself (though you can).

After you place your script in /etc/init.d and make it executable, if you run the command:
```
sudo update-rc.d *scriptname.sh* stop 6
``` It will create the appropriate symlink in /etc/rc6.d for you. If you ever want to remove everything, just delete the script from /etc/init.d and then issue the command:
```
sudo update-rc.d *scriptname.sh* remove
```This is the 'approved' way. It's just as easy to do it manually if you are only dealing with one runlevel but it's pretty handy when adding links to multiple runlevels.

tgeer

---

### Post by madu on 2009-08-20
Thank you tgeer43.

I tried your way but gave me an error.
```
root@desktop:/etc/init.d# sudo update-rc.d reminder.sh stop 6
update-rc.d: warning: /etc/init.d/reminder.sh missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
Use of uninitialized value within @ARGV in string ne at /usr/sbin/update-rc.d line 222.
update-rc.d: error: action with list of runlevels not terminated by "."
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force

```

Also should I be using rc6 or rc0 or it doesn't matter? Excuse my lack of knowledge in this regard.

Thank you.

---

### Post by tgeer43 on 2009-08-21
Oops - three errors in my last post. [blush]

1. There should be a two digit number between 'stop' and the runlevel number. This is the sequence number and determines when in the sequence of shutdown scripts for that runlevel your script will be executed. Each link created with update-rc.d will have a filename of the form: SNN*yourscriptname* (eg. S06reminder, so just look in /etc/rc0.d for an appropriate sequence number. You'll want to use a low number that is not already in use so that you reminder will display before the Xserver shuts down.

2. The command line should be terminated by a space and a period '.'

3. The correct runlevel for shutdown is 0 (6 is for a reboot).

So the correct command should be:
```
sudo update-rc.d reminder.sh stop NN 0 .
```Where NN is the sequence number that you have selected.

Sorry about that. I guess that's what happens when you've been up for 36 hours. :wink:

tgeer

---

