---
title: "Can't copy files?"
date: 2010-03-02
forum: General Help
---

### Post by Scooter_X on 2010-03-02
](*,) So lately I've been trying to get a couple of programs up and running, and I've been told that to do so I need to copy or extract a certain file to a certain location. Every time I try to do that, I get a 'permission denied' or something similar. I'm trying to move a file into  /etc/udev/rules.d and that's the error I get. I don't understand. Why does it keep doing this to me? Why wouldn't I have access to anything other than my home folder? Do I have to be a member of a certain group? I already checked, I'm a member of Admin... I don't get it. Any help would help me greatly. Thanks.

---

### Post by Scooter_X on 2010-03-02
When trying to install software or modify something, often times I am asked to move a certain file that I create as follows:

> 3. Create a file called 45-legonxt.rules using your favorite text editor.  Its contents should look like this:

SUBSYSTEM=="usb_device", ACTION=="add", SYSFS{idVendor}=="0694", 
SYSFS{idProduct}=="0002", SYMLINK+="legonxt-%k", GROUP="legonxt", MODE="0660", RUN+="/etc/udev/legonxt.sh"

4. Copy this file to /etc/udev/rules.d.  From a terminal prompt type

sudo cp 45-legonxt.rules /etc/udev/rules.d

But when I do that I get the error that it doesn't know where "45-legonxt.rules" even IS. I don't understand! I even included the ENTIRE directory with the file, just to see. And nothing. Why do so many people say to copy files in this manner if every time the computer isn't able to even find the file?

---

### Post by leg on 2010-03-02
> **Scooter_X said:**
> ](*,) So lately I've been trying to get a couple of programs up and running, and I've been told that to do so I need to copy or extract a certain file to a certain location. Every time I try to do that, I get a 'permission denied' or something similar. I'm trying to move a file into  /etc/udev/rules.d and that's the error I get. I don't understand. Why does it keep doing this to me? Why wouldn't I have access to anything other than my home folder? Do I have to be a member of a certain group? I already checked, I'm a member of Admin... I don't get it. Any help would help me greatly. Thanks.You will need to be root to edit that file so load it up using sudo. I think you can use the gk version:

```
gksudo gedit <filename> &
```

The ampersand allows you to use the terminal for something else if you want. If you don't need that don't add it. You will have to enter your password after that. You can also do it like this:

```
sudo nano <filename>
```if you want. I think I have entered the commands properly.

---

### Post by Pritamsng on 2010-03-02
ya ... you should have root privilege.. as normal user its not possible to edit system file.

---

### Post by Morbius1 on 2010-03-02
> 3. Create a file called 45-legonxt.rules using your favorite text editor.So far so good but he doesn't tell you where to save it. 
> 4. Copy this file to /etc/udev/rules.d.  From a terminal prompt type

sudo cp 45-legonxt.rules /etc/udev/rules.d When you open a Terminal it's default location is /home/username. If you saved the file to /home/username/45-legonxt.rules you'd have a better chance.

Or if he had stated to create the file using an editor as root or gksu then you could have saved it to the correct location without going to the terminal.

---

### Post by Olav on 2010-03-02
The file is located in the directory where **you** created it. For instance, if you created it on your desktop these are the commands you would give:
```
$ cd ~/Desktop
$ sudo cp 45-legonxt.rules /etc/udev/rules.d 
```
Minus the "$" of course, that only represents the prompt you see in your terminal.

Now a word of caution. If you are unsure what you are doing, blindly pasting commands in a terminal window can be a [dangerous]("http://ubuntuforums.org/announcement.php?f=331") thing. Especially everything preceded by the sudo command can leave your system in an unusable state. By placing things in /etc/udev/rules.d you are changing some of the inner workings of the operating system. Be careful that you know at least how to reverse any changes you make.

I think at the very least you should familiarise yourself with the basic commands you can use in the terminal. [This]("http://linux.org.mt/article/terminal") seems to be a nice introduction course, but there are many more if you google for them. Commands like ls, cd, cp, rm, mv, man, less, cat, etc. are simple enough, but knowing them well can safe your life in many cases.

---

### Post by Scooter_X on 2010-03-02
What I'm trying to do is copy a file to /etc/udev/rules.d. Should I then:
sudo nano /etc/udev/rules.d?

I have gotten the following response:
Riley is not in the sudoers file. This incident will be reported. 

And nothing happens. I got the same response when I just tried to straight up copy: 
sudo cp 45-legonxt.rules /etc/udev/rules.d

What is that telling me? Did I do it correctly? I also tried:
sudo nano new-file 

and got:
sudo nano new-file

 * Downloading details about the software sources... 
 * Downloading list of packages.. 

[1]+  Done                    gksudo gedit new-file

So, yea. I guess I'm still lost. Sorry.

---

### Post by Scooter_X on 2010-03-02
Ah-HA!! That's good to know. /home/username. I'll remember that. Thank you very much.

Edit: I just barely noticed Olav's post after I wrote a reply. so if I cd to my desktop or to wherever I created the file, THEN do a copy, it understands which file I'm talking about. If I don't cd to anything when I first open up a terminal, then it'd likely be /home/username. At least that's my assumption. Correct me if I'm wrong. And thanks for posting that Olav. Especially the bit about the $, because I never knew what in the heck that meant.

---

### Post by Enigmapond on 2010-03-02
Have you tried..

```
gksu nautilus
``` 

This will give you temporary root browsing and you can just simply copy or extract the file and put it anywhere.

---

### Post by Scooter_X on 2010-03-02
> **Enigmapond said:**
> Have you tried..

```
gksu nautilus
``` 

This will give you temporary root browsing and you can just simply copy or extract the file and put it anywhere.

It says 'command not found'....? Dang.

---

### Post by Enigmapond on 2010-03-02
Ok...try then...

```
gksudo nautilus
```

---

### Post by Morbius1 on 2010-03-02
You by any chance not using Gnome? Nautilus is the Gnome file manager.

---

### Post by Elfy on 2010-03-02
threads merged - please do not post duplicates

---

### Post by Morbius1 on 2010-03-02
Let's say you created the original file and saved it to:

[B]/home/scooter/45-legonxt.rules

[/B]The complete and unambiguous way to copy that file to the desired location is:[B]

sudo cp [/B] [B][COLOR=Blue]/home/scooter/[/COLOR]45-legonxt.rules /etc/udev/rules.d

[/B]The thing about opening up the terminal is that by default it opens to  [B][COLOR=Blue]/home/scooter/

[/COLOR][/B][COLOR=Black] Since that's where you saved it you can shorten the copy command to:[/COLOR][B][COLOR=Blue]
[/COLOR][/B]** sudo cp ****45-legonxt.rules /etc/udev/rules.d**

Had you saved it somewhere else you need to "cd" to that location first to use the "shortened" way or use the "unambiguous" way.

Am I making this explanation worse?:p


[B][COLOR=Blue]

[/COLOR][/B]

---

### Post by Scooter_X on 2010-03-02
Morbius 1- you merely solidified what I had tried feebly to explain

forestpiskie - sorry I didn't know I duplicated.

and YES!! the gksudo nautilus DID in fact work. Cool. Thank you tons! I got my file copied over and I'm on to the next step of this thing I'm trying to set up.

So basically whenever I have to modify some files, I can run 'gksudo nautilus' to copy/paste/delete whatever I need. 

Now I just gotta' go find out what this gksudo thing means specifically... I understand that SUDO gives me root access to do uber-administrative stuff, but gksudo... hmmm...

anyways, thanks again everyone for helping out on this. I appreciate it.

-Scooter

PS- do I have to worry about UN-SUDOING that window? Or does it just shut off the root access when I close the window?

---

### Post by Enigmapond on 2010-03-02
It will return to normal when you close that Nautilus window...

Glad to help.

Cheers!

---

