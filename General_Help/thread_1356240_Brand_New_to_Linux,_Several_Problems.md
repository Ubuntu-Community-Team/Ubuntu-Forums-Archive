---
title: "Brand New to Linux, Several Problems"
date: 2009-12-15
forum: General Help
---

### Post by knietzsche on 2009-12-15
I got rid of Vista and installed Ubuntu 9.10 instead.  There are several things that i really need for ubuntu to be something i will stick with. 

-Adobe flash player doesn't work.  I'm using a 64 bit machine and adobe doesnt offer an official 64 bit version that i see.  I looked for versions on the net elsewhere but there is either an error after installation that it can't find the file or it asks me to turn script into an executable.

-I don't know how to make executables.  I found that you are supposed to "chmod 755" the file.  I tried opening terminal and typing chmod 755 adobefilename and it can't find it.  I cant even change directory to my personal folder.  I can "cd /home" but when i try to "cd /kevin" it cant find the directory even though i have clearly inspected that the kevin folder is inside the home folder.

-Itunes doesn't work.  I found some place on the internet that told me to install wine and gave me a list of commands to do.  I did as it says but after installation if i click on the itunes icon it tells me that I installed it wrong.

Can anyone help?

---

### Post by Iowan on 2009-12-15
> **knietzsche said:**
>  I cant even change directory to my personal folder.  I can "cd /home" but when i try to "cd /kevin" it cant find the directory even though i have clearly inspected that the kevin folder is inside the home folder."cd /kevin" assumes the folder is just off the root directory.
 "cd /home/kevin" should get you into the directory. 
Hint: "cd ~" or simply "cd" will get you to your home directory.
[This]("http://ubuntuforums.org/showthread.php?t=1353902") thread also discusses the topic.

---

### Post by darco on 2009-12-15
Adobe does have a native 64 bit flash...I have attached a zip file. Just extract, click and choose run in terminal, the script will do the rest....works like a charm!

good luck

darco

---

### Post by Ordes on 2009-12-15
1. Dont know about the flash as i dont run a 64-bit.

2. When you are alredy in /home.. Than u dont need  /  in front of Kevin. The command would just be cd kevin. 
/  in the beginning of the command refers to your root directory.. so $cd / will put u to your root dir, in which where is home, bin, etc.. So when u enter cd /kevin.. The system understands this as root > kevin... like cd /home... root > home.
Different when u write out the whole command. like  cd /home/kevin .. Only the first / refers to root. 
A good way to see if your command is right, or to write long command chains, and u dont remember the file hierachy, is to use "tab" for autofill, if your folders/ files are not getting autofilled, or u dont get a suggestion, becuase of multiple choices, than there is a problem with the command order itself.for

3. Again, i dont use Itunes. But from all my friends i heart that it doesnt work well with wine. Even when it has a silver on winehq. Perhaps this helps [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10248](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10248), they recommend to install it as Win2000 app in wine.
However, my friends prefer gtkpod, for the ipod managment.

---

### Post by knietzsche on 2009-12-15
/sigh

kevin@Nietzsche:~$ (i pressed tab)
Display all 2231 possibilities? (y or n)
kevin@Nietzsche:~$ cd /home
kevin@Nietzsche:/home$ (i pressed tab)
Display all 2231 possibilities? (y or n)
kevin@Nietzsche:/home$ cd kevin
kevin@Nietzsche:~$ (i pressed tab)
Display all 2231 possibilities? (y or n)
kevin@Nietzsche:~$ 

I must be way off base.


Hitting tab shows the available files in the directory i am in, correct?  because it always 2231 possibilites thats means i never changed directory.  also, the command  "cd kevin" seems to take me out of home?

I'll try to run the adobe script file when i can mess with terminal :(

---

### Post by Iowan on 2009-12-15
> **knietzsche said:**
> 
kevin@Nietzsche:[COLOR="Red"]~$[/COLOR] (i pressed tab)
Display all 2231 possibilities? (y or n)
kevin@Nietzsche:[COLOR="Red"]~$[/COLOR] cd /home
kevin@Nietzsche:/home$ (i pressed tab)
Display all 2231 possibilities? (y or n)
kevin@Nietzsche:/home$ cd kevin
kevin@Nietzsche:[COLOR="Red"]~$[/COLOR] (i pressed tab)
Display all 2231 possibilities? (y or n)
kevin@Nietzsche:[COLOR="Red"]~$[/COLOR] 
The highlights ([COLOR="Red"]~$[/COLOR])show that you are already in your home folder. 
**pwd** will give you the full path (probably /home/kevin).

---

### Post by knietzsche on 2009-12-15
> **Iowan said:**
> The highlights ([COLOR=Red]~$[/COLOR])show that you are already in your home folder. 
**pwd** will give you the full path (probably /home/kevin).

muahaha i was in /home/kevin the whole time.

---

### Post by oldsoundguy on 2009-12-15
9.10 no longer requires chmod 777 to make a file executable ..

Drag the file folder to the Gnome desktop, right click and select properties, click on permissions tab and grant same!  DONE!

Then double click on the file and it will launch and install.

---

### Post by daenoid on 2009-12-15
> **knietzsche said:**
> -Itunes doesn't work.  I found some place on the internet that told me to install wine and gave me a list of commands to do.  I did as it says but after installation if i click on the itunes icon it tells me that I installed it wrong.

I've not heard of any decent results from running iTunes under wine. Your best bet is to install Banshee and work with gtkpod. Unfortunately not all iPod versions are supported under gtkpod, but if it is you should be able to plug your iPod up and banshee will ask you to sync.

---

### Post by Agent ME on 2009-12-15
> **knietzsche said:**
> /sigh

kevin@Nietzsche:~$ (i pressed tab)
Display all 2231 possibilities? (y or n)
kevin@Nietzsche:~$ cd /home
kevin@Nietzsche:/home$ (i pressed tab)
Display all 2231 possibilities? (y or n)
kevin@Nietzsche:/home$ cd kevin
kevin@Nietzsche:~$ (i pressed tab)
Display all 2231 possibilities? (y or n)
kevin@Nietzsche:~$ 

I must be way off base.


Hitting tab shows the available files in the directory i am in, correct?  because it always 2231 possibilites thats means i never changed directory.
Just pressing tab with nothing typed in will make it try to list every possible command. Try typing "cd ke<tab>" and see it fill in the rest for you. If nothing comes up the first time when you press tab, that means there's either nothing possible for those letters or there are several things possible -- in this case, press tab a second time and it will list the possibilities.

---

### Post by staf0048 on 2009-12-15
I think the others hit on your 1st two issues pretty well, so I wont delve into those.  However, as for your iTunes problem you have a couple of options.

Install PlayOnLinux - I think it's in the repos, but if not just do a google search and get it from the web.  PlayOnLinux is a really cool Wine wrapper that will configure your programs perfectly to work with Wine.  There are tons of programs listed that it will help you install properly - including iTunes.  I'd try this first if you're absolutely devoted to iTunes.

However, IMHO, while you're making the switch to an open platform, why not use an open alternative to iTunes.  I use Rhythmbox, which is installed by default and it worked more or less perfectly with my 1st and 4th gen nanos with out any special work on my part (except album artwork was a hassle).  I've tried other programs and did not see any better performance or ease of use than Rhythmbox, so I've stuck with it.  

Good luck!

---

### Post by Ordes on 2009-12-15
@autofill - tab

when u hit tab without having typed anything it will list u all possibilities....

go into your terminal

$ cd /   and now hit tab (twice for choices)
you will see it only lists the folders in /


now try 
$ cd /ho [tab] and it will become cd/home/ 
now keep on typing   $cd /home/k [tab] and it should become cd/home/kevin
unless u have another folder starting with k in there...

another try
$cd /s [tab] and it will list u all possible choices in / with s
as the second letter should be differnt for all the listed folders, u just need to enter one more letter, like $cd /sy [tab] and it will become cd /sys

hope this clears it up ;)

---

### Post by fluffman86 on 2009-12-15
1. I always install flash on my 64bit system by going to Applications > Ubuntu Software Center.  Go to Edit > Software Sources > Check the first 4 boxes.  Then back in Software Center, click View > All Applications.  Then search for "flash" and the first options should be "Ubuntu Restricted Extras" which you can install by double clicking.  This includes flash, mp3, java, etc. support.

2. Tab is used to autocomplete.  This means that if you haven't typed anything, then there is a possible 2,000-some-odd commands that you can attempt to run.  Instead, type "ls" and press enter to view your folders.  Then, if you want to CD into one of them, you can type "cd Doc" then press tab, and it will autocomplete the word "Documents."  Or, if you can't remember then name of a long command, like "ecryptfs-unwrap-passphrase" or something, you can type "ecryptfs" and press Tab twice to see all of the available ecryptfs commands.

Also, when you open terminal, you'll see something like
```
kevin@kevin-desktop:~$
```
This is the command prompt...it's prompting you for command input.  The first "kevin" is your current username, "kevin-desktop" is what computer you're at.  This is important, because sometimes people will sit at one computer and "ssh" or remotely control another computer.  

The tilde (~) is a shortcut for your current users home directory.  So if you type "cd ~/Documents", it is the same as typing "cd /home/kevin/Documents".  Some other useful shortcuts:
"cd" with no other directories will take you straight to your home directory.  Same as "cd ~" or "cd /home/username"
"." - a single dot refers to "this directory" so if you want to run a program that's only in your home directory instead of installed for the whole system, you need to type "./programname" after you cd into your home directory.
".." - two dots mean "up one directory" so if you are in /home/kevin/Documents/schoolwork, then you can type "cd .." to take you to /home/kevin/Documents

The dollar sign ($) means you are currently a normal user.  If you were to become root (useful for some other versions of linux, but not necessary in ubuntu), then the $ would change to #.  

3. Itunes is really pretty useless in linux.  I've never gotten it to work well.  Instead, I use banshee.  You can find it in Applications > Ubuntu Software Center.  It's great for managing some of the older ipods.  Rhythmbox is installed by default can manage music, but Banshee can do podcasts and video as well.

If you need iTunes for your iPhone, then you are simply out of luck.  You'll always need to boot into windows to run system upgrades, but you can look into a program called virtualbox which allows you to run a full install of Windows within Ubuntu.  VirtualBox + Windows + iTunes works great for syncing your iPhone and installing apps and browsing the app store, but it *WILL DESTROY YOUR IPHONE* (last I heard) if you do a major firmware upgrade on the iphone.  The reason why is that the iphone reboots part of the way through the update, which disconnects the USB interface.  This is fine if you are running Windows natively, but VirtualBox doesn't know to automatically reconnect the iPhone quickly enough, which causes the update to fail, which bricks your iPhone, at least temporarily.

---

### Post by knietzsche on 2009-12-15
Thanks a bunch all, i think i got a better feel for it now. 

Im install flash player now, its a lot easier when you dont have to use chmod.  I guess i'll settle for banshee then, it does sync with my ipod.

The main reason i wanted itunes is because all of my music is on my ipod and no where else.  It was on vista but i wiped it.  To get the files from the ipod onto the computer they are just random letters

If i run it through itunes on a windows pc, it will change the names back to normal?  And then i can transfer them over to my ubuntu machine.  Anyone know a better way?

---

### Post by fluffman86 on 2009-12-15
Just plug your ipod into your ubuntu computer, open banshee, and you'll see all of the files on it.  You can them sync your ipod and all of your files will go to /home/kevin/Music.

---

### Post by ramjet_1953 on 2009-12-15
If you are still having problems with Flash, just follow the link below:

[http://www.omgubuntu.co.uk/2009/12/64bit-flash-ppa.html](http://www.omgubuntu.co.uk/2009/12/64bit-flash-ppa.html)

It will help you to install the new 64 Bit flash plug-in.

Regards,
Roger :)

---

### Post by steveneddy on 2009-12-15
If you are in another folder than /home then the command to go /home in terminal is simply

```
cd
```

then to see the list of files in that folder type in terminal

```
ls
```

To go to another folder, say the Desktop, in the /home folder for example you would

```
~/Desktop

```

Also see the links in my sig for further instructions on many other subjects.

---

### Post by knietzsche on 2009-12-15
> **fluffman86 said:**
> Just plug your ipod into your ubuntu computer, open banshee, and you'll see all of the files on it.  You can them sync your ipod and all of your files will go to /home/kevin/Music.

i dont see a sync but i clicked import from media and selected my ipod.  It "synched" and now displays my songs in banshee but they do not play and there are no songs in my music folder.

---

### Post by staf0048 on 2009-12-16
I'd try Rhythmbox if I were you.  Even if you don't end up using it as your default audio player, it will recognize your iPod with the correct track names, artits, etc.  I think it pulls up the files with in the main window once it's connected (if not just select the iPod on the left hand side.  Then you can either select all and move to your library (top left side on Rhythmbox) or just copy and paste into your music folder.  Either way should work.

To put songs onto your iPod from Rhythmbox, just drag and drop.  Easy peasy if you ask me.

---

