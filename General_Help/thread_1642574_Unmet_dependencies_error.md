---
title: "Unmet dependencies error?"
date: 2010-12-10
forum: General Help
---

### Post by JohnnyDohable on 2010-12-10
Hello,

I'm relatively new to Ubuntu.  I've looked around for problems like mine, but haven't really found one.  It's been sort of an evolving process.

First thing that happened is that I could not use Firefox.  Later, other programs would not work.  I can't run Software Center and a few other programs.  Now, I have a red circle in the top right hand corner that says "An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.  The error message was: 'Error: Opening the cache (E:Read error - read (5: Input/output error), E:The package lists or status file could not be parsed or opened.)'This usually means that your installed packages have unmet dependencies"

When I run Synaptic Package Manager, it loads for a while, then displays an error box that says a similar thing to this.  When I try apt-get in Terminal, it says it can't do something because of a lock open file.  "13: Permission denied"

Thanks if someone knows about this

---

### Post by searchfgold6789 on 2010-12-10
In a terminal: ```
sudo apt-get -f check
```
Type in your password which will not appear and press enter.
Read us the output.

---

### Post by JohnnyDohable on 2010-12-10
Thanks I typed in the command in terminal.

It said "Reading package lists..."  It stopped at 6% for a while.  This was followed by an error message:

"E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened."

---

### Post by JohnnyDohable on 2010-12-11
I don't know if this is relevant, but I have a dual boot...  I have Ubuntu and Windows XP.  My Windows XP has been showing the blue screen of death lately.  It will start up fine, but then freezes up and going to the blue screen and says I should disable my BIOS shadowing or caching... or something like that.  I doubt that the two problems are related, but I am not sure.

---

### Post by sikander3786 on 2010-12-11
Try using an older status file.

Backup the existing one:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```

Setup the old one to be used:

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

And then post the output of this command.

```
sudo apt-get update
```

---

### Post by JohnnyDohable on 2010-12-12
On the second instruction, terminal says that the file /var/lib/dpkg/status doesn't exist.

---

### Post by sikander3786 on 2010-12-12
Post the complete output of this one.

```
ls /var/lib/dpkg
```

---

### Post by JohnnyDohable on 2010-12-12
"ls /var/lib/dpkg
**alternatives**  cmethopt  **info**  statoverride  statusold
available  diversions  lock statusoverride-old   **triggers**
available-old  diversions-old  parts  status.bad  **updates**
"

---

### Post by sikander3786 on 2010-12-12
I don't know why it is named statusold instead of staus-old as it normally does.

Anyhow, try these commands.

```
sudo cp /var/lib/dpkg/statusold /var/lib/dpkg/status
```

```
sudo apt-get update
```

---

### Post by JohnnyDohable on 2010-12-13
Well this doesn't seem to make sense, because I saw your logic.  After I entered the first line into terminal it said:
"cp: cannot stat '/var/lib/dpkg/statusold': No such file or directory"

I tried to go on ahead with the second line you gave me and it didn't work, saying something similar.

---

### Post by JohnnyDohable on 2010-12-13
> **sikander3786 said:**
> I don't know why it is named statusold instead of staus-old as it normally does.


Oh wait, now I think I see the problem.  When I printed the complete output of the ls command, I believe I typed "statusold".  I thought this was actually correct at first, but I just did the ls command again, and this time it says "status-old" instead of "statusold".  So...  think it actually is named status-old rather than statusold.

But I'm not exactly sure what to do now...

---

### Post by sikander3786 on 2010-12-13
If stauts-old is there, unless you are typing it wrong, this command *_should_* work.

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

If possible, just copy paste the command from browser to your terminal. I suspect if you are making in mistake while typing it.

---

### Post by JohnnyDohable on 2010-12-13
Ok, I did it and I think it worked.  Now what should I do?

---

### Post by JohnnyDohable on 2010-12-13
Wait.  Actually, I just did sudo apt-get update command and my red error circle has gone away.  I think I'm going to go around and see if some of my programs work now.

---

### Post by JohnnyDohable on 2010-12-14
Ok, so after the red circle went away, an update manager popped up and I tried updating.  The update went mostly successfully...  However some things were not successful.

Some of my programs still did not work.

I tried starting Ubuntu the next day, and it did not work...  It went to a black screen and said something that I don't remember right now...  Anyways, I restarted the computer and booted up my other Ubuntu...  I think it's an older version boot up...  Or something like that.  Anyways, there is no red circle on this one either, but my programs still don't work.

---

### Post by sikander3786 on 2010-12-15
So which of your programs are not working? What happens when you try to open them?

And your other Ubuntu install is broken? It is giving you just a black screen or what?

Which graphics card is there? And I hope this is a proper install with Ubuntu on its own partition or it is a Wubi install inside WIndows?

---

### Post by JohnnyDohable on 2010-12-16
It is Ubuntu on its own partition.

Here is exactly what is happening now:

When I attempt to start Ubuntu, I get a black screen that says something like "error: unable to read file" and below that line it says "You need to open the kernel first" or something like this.  Sorry it's hard to remember it and type it down...  I'm using Windows XP Safe Mode now, since my normal Windows is also messed up.  But that is not important right now.


EDIT:  Fixed the start up messages.

---

### Post by JohnnyDohable on 2010-12-16
The programs that don't run are not limited to:

Firefox, Ubuntu Software Center, Movie Player, Sound Recorder, and pretty much all sound & video program, Limewire, Empathy...

Programs that work are Chromium and Midori and qBittorrent and OpenOffice...  Maybe some others.

---

### Post by sikander3786 on 2010-12-17
Try fixing any broken packages/dependencies.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by JohnnyDohable on 2010-12-17
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up grub-pc (1.98-1ubuntu9) ...
Installation finished. No error reported.
cp: reading `/usr/share/grub/unicode.pf2': Input/output error
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)

This is the code I receive after entering the sudo apt-get install -f code.

---

### Post by pichita on 2013-03-08
> **sikander3786 said:**
> Try using an older status file.

Backup the existing one:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```

Setup the old one to be used:

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

And then post the output of this command.

```
sudo apt-get update
```

Thanks. This worked like a charm!

---

