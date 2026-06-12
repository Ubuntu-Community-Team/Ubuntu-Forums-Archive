---
title: "Accesing Files from Remote  Computer"
date: 2009-09-15
forum: General Help
---

### Post by Mercenary(FH) on 2009-09-15
wasn't sure if this was right section or not


So I just installed ubuntu 9.04 (w/e the newest one is)
Im not a complete newb at linux. just the desktop part of it (I know the commands lol)

With that being said I have looked all over google but keep getting the wrong things.

I have 2 computers, a laptop and a desktop at home with ubuntu 9.04 on them. At least I think it's 9.04......I used Wubi to install them both (seemed to work fine)

ANYWAYS
Basically I want a Folder on my desktop at home. that has files that I can access from my laptop (via ssh or w/e)
Basically I'd put files in here that I may need (Programming files/stuff I may forget and need at school)

I'd be accessing them from my laptop (which i use at My university) and be able to copy them from the desktop to the laptop

I installed SSH on my computers, i'd obviously need to know the IP address of my home computer but I have NO clue what to do? I'd assume I set up a sharing folder on my desktop computer but then what? any help would be super greatly appreciated thxxx

---

### Post by conehead77 on 2009-09-15
if you want to access the computer with SSH, there is no need to make a shared folder. You log into the remote box with
```

ssh username@ipaddress

```
after the password confirmation you can access all files on the remote computer.

to copy from desktop to laptop look up the scp command.

maybe a SVN/Git/whatever-repository would fit your needs.

or sign up for ubuntu one [https://one.ubuntu.com/](https://one.ubuntu.com/) to share up to 2GB like a shared folder.

personally i use ssh and modify the content on the desktop without copying to the laptop or the SVN method with a SVN server from my university. you would need to install the SVN server on your desktop which might take some time if you have no experience in stuff like this.

---

### Post by Mercenary(FH) on 2009-09-15
Can I copy files from the computer I SSH to?
or no?

and is there anything wrong with using SSH to copy files?

---

### Post by conehead77 on 2009-09-15
> **Mercenary(FH) said:**
> Can I copy files from the computer I SSH to?
or no?

and is there anything wrong with using SSH to copy files?

yes, scp uses ssh to copy files from the desktop to laptop. with scp you need **not** log in with SSH first.
Just run

```

scp username@ipaddress:/home/username/somefile.txt .

```

the dot indicates that you want the file to be copied to the current directory but you can use every path you want

edit: there is nothing wrong with copying files with ssh. you should obviously choose a strong password. with svn or ubuntu one you would need no ssh and thus no stranger could possibly connect to your desktop via ssh.

---

### Post by Mercenary(FH) on 2009-09-15
ill need to disable firewall on the other  computer wont i?
altho since both comps are running ubuntu i dunno im a nub

---

### Post by conehead77 on 2009-09-15
> **Mercenary(FH) said:**
> ill need to disable firewall on the other  computer wont i?
altho since both comps are running ubuntu i dunno im a nub

what is the error message?

---

### Post by Mercenary(FH) on 2009-09-15
o i hadn't tried it yet. just an observation

---

### Post by conehead77 on 2009-09-15
> **Mercenary(FH) said:**
> o i hadn't tried it yet. just an observation

ah, i see :)

ssh runs on port 22, so that shouldnt be blocked...
but usually it should work just fine without twiddling any settings

if you have trouble, a look at the files /etc/hosts.allow and /etc/hosts.deny might help

---

### Post by Mercenary(FH) on 2009-09-15
thx a ton man. didnt know it'd  be so easyyy

---

### Post by Mercenary(FH) on 2009-09-16
actually I got a connection refused error when I try to ssh to it.

edit: nm i figured  it out. post 22 wasn't forwarded on the roouter.


with that being said I guess i use the CP command in the terminal to copy stuff?
is there any kinda GUI interface? that lets me do the same thing?

---

### Post by nothingspecial on 2009-09-16
ssh with x

```
ssh -X user@ip
```

Then run nautilus

---

### Post by P4man on 2009-09-16
to copy files over ssh, you need scp. (assuming you want to copy from the remote to the local machine or vice versa, and not just copy remotely to the same remote machine):

have a look here:
[http://www.linuxtutorialblog.com/post/ssh-and-scp-howto-tips-tricks](http://www.linuxtutorialblog.com/post/ssh-and-scp-howto-tips-tricks)

For a gui, try secpanel (never used it myself)

edit:nothing special's idea is neat too. Never thought of that :)

---

### Post by Mercenary(FH) on 2009-09-16
> **nothingspecial said:**
> ssh with x

```
ssh -X user@ip
```

Then run nautilus

what exactly does the -x do?
and what is nautilus?
(sorry im a huge nub)

and I thought you could copy files? from SSH (using the copy command in the terminal)? I would be copying files from my desktop onto my laptop (i'd be using my laptop from school and have ssh running on both but i'd be taking files FROM the desktop)

Because I could see the files? why couldn't i copy them? someone else previously said that I could?
:confused:

edit: Also for security reasons is there a simple way to turn SSH on and off so I can keep it on when I need something but turn it off when i dont need anything?
Im new to ubunutu so The commands im familiar with but I dont understand alot of stuff (but im learning)

---

### Post by nothingspecial on 2009-09-16
The X (it has to be a capital X) forwards the X session to the remote machine, allowing you to run gui apps on a remote computer.

Nautilus is your default file browser. You know, the thing that opens when you click on Places or Documents.

So just type ```
nautilus
``` after you have run ```
ssh -X user@ip
``` and the files on your remote pc will appear in a window and you can drag them to your Desktop or Pictures, Videos etc on the pc you are at.

Cool eh?

---

### Post by nothingspecial on 2009-09-16
Sorry didn`t see second part of your post. For security you don`t need to turn ssh off. You need to read [[COLOR="Magenta"]this[/COLOR]]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

---

### Post by Mercenary(FH) on 2009-09-16
the other question was?
Can I or can't I copy files using normal ssh 

ie ssh blah@blahhhhh
and then use the CP command? to copy the files?


i've heard yes I can but then you just said no i couldn't :(

---

### Post by Mercenary(FH) on 2009-09-16
or would I have to use another program to copy? because I dont mind doing it from command line

---

### Post by nothingspecial on 2009-09-17
You ssh into the remote computer. Then

```
scp -rv /path/to/file username@ip.of.computer.you.are.sitting.at:/where/you/want/to/save/it
```
for example

```
scp -rv ~/Music/nice.mp3 john@192.168.1.1:/media/backup_drive
```
Or do it the other way around. I`ve usually sshed into the remote computer to search for the file that`s why I showed you this way.

the r is only necessary if it`s a directory you are copying so you don`t need it in this example, I just put it in to show you.

the v stands for verbose, ie it will tell you what it`s copying, at what speed and how long till it finishes

---

### Post by Mercenary(FH) on 2009-09-17
Ok I understand now.
thx a ton. Im learning alot from the forums from ppl like you :)
:popcorn:

---

