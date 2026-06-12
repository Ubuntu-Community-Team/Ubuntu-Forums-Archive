---
title: "AIM on linux"
date: 2006-05-21
forum: General Help
---

### Post by cobbweb on 2006-05-21
I would like to make it so  I can install AIM Messenger by typeing something like this ...

 sudo apt-get install aim 

 just the standard way to install programs. I don't know how to add somthing to the list of places it will download from and install. I found the program on [http://www.aim.com/get_aim/linux/latest_linux.adp#deb2](http://www.aim.com/get_aim/linux/latest_linux.adp#deb2)

Is there a solution to my problem? or will i have to download and install it manually. Any help is welcome, thank you,

 Cobbweb

---

### Post by bikeboy on 2006-05-21
If you have downloaded the .deb like it says on the site it's just as easy as the apt-get method, only different.

Change to where you downloaded the .deb then: ```
 sudo dpkg -i <name.deb>
```

You can always use gaim to login to aol anyway.

---

### Post by jones_jj on 2006-05-21
cobbweb, have you checked out the universal repositories in synaptec to see if AIM is there?  When you launch synaptec, go settings->repositories and make sure you have the universal repository listed.  Then you should be able to get AIM.

---

### Post by dust0r on 2006-05-21
will gaim import a budylist?

---

### Post by jones_jj on 2006-05-21
Yes it will.  Just start Gaim, add the appropriate account (chat protocol, username, and password) and as soon as you click connect you will have your buddy lists for AOL.

---

### Post by stanz on 2006-05-25
I likes gaim, ayttm...there fine- 'cept for doing the cam thing.
I've not been able to work it out ~ being newbie, has much to do wit that.
I Cannot find aim in the repos,
[quote="jones"]->repositories and make sure you have the universal repository listed.[/quote]
Thanks for that tho...I got more gaim extent's....
Aim's page ~ to get the deb...gives a funky looking page, that don't help.
I couldn't copy-n-paste- to show ya...it seemed froze...?
Also...right-click on deb....to choose...save as~~?...not work either !

I donno.... & can't figure or work out the tgz file... jus' ain't learnt it yet ~*

Any advice or help ?  This REALLY would stop some long distance tele calls!!

---

### Post by nalmeth on 2006-05-25
search packages.ubuntu for AIM possibly?
to compile tarballs you need build-essential installed.
There are many howto's instructing how to compile apps, search the forums.

---

### Post by stanz on 2006-05-27
[quote=jones_jj]...checked out the universal repositories in synaptec to see if AIM is there?  When you launch synaptec, go settings->repositories and make sure you have the universal repository listed.  Then you should be able to get AIM.[/quote] I take it, your saying...~ it IS there?
I can only find reference to a 'jabber-aim' package plugin.
Clicking the deb link-[ this aol's page]("http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb") [careful here- it takes time]..responds::
> !<arch>debian-binary   1042953733  0     0     100644  4         `2.0
control.tar.gz  1042953733  0     0     100644  4369      `
&#65533; 
Is Something NOT right here?
There is no 'right-click', save file as...
The 'rpm & tgz' files, pass the normal response.
But- A page like that ~ is new to me. So i'm unable to work this out- 
or know how to get the deb.      ](*,)

Is this jus' me?
[This is that webpage..]("http://www.aim.com/get_aim/linux/latest_linux.adp?aolp=")

---

### Post by stanz on 2006-05-27
> Installation Instructions for TGZ (All other OS)
1.      Log in as root.       
2.       cd /       
3.      Download AIM onto your system        
4.      On the command line, type gunzip command as shown in the example: gunzip -c aim-1.5.286.tgz | tar xvf -,
where 1.5.286 represents the AIM version and release numbers       
5.      To run AIM, log in as a regular user, and type "/usr/local/bin/aim" on the command line. I can only get the tgz...as per above post...
**1-2-3**..Download as root?
_I downloaded as user_.. copied into root's  home, made new 'download' folder.
**Did #4**, here's some output:
[I]./
./usr/
./usr/bin/
./usr/bin/aim
./usr/lib/
./usr/lib/aim/
./usr/lib/aim/CoolBos.so[/I]
**Ran #5, **:[I] ~$ /usr/local/bin/aim
bash: /usr/local/bin/aim: No such file or directory
[/I][B]This was right, - file was empty, so i pasted the 'bin' file in there.
Again ran #5,[/B][I]:~$ /usr/local/bin/aim
/usr/local/bin/aim: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
[B]I'm finding aim or the gunzip command- is unpacking the files in the same directory[ or folder]...not where there supposed to go.
[/B][/I]as in* "/usr/local/bin/aim" *- not put in the* '/usr/local/bin' folder ! ?*
also, remaining in the download folder: is aim's:
-the *usr* folder, having in that: *bin* &* lib* , folders.
-the *bin* folder- having the *bin* file....
-the *lib* folder- having the *shared libs*..and another aim folder.
](*,)       ](*,)
I'm trying to figure this out... if i'm right in placing the bin file- where i did.
and before i go placing libs- all over... I'ld ask for someone to lend some advice!
Anyone..?  :D

---

### Post by Harold P on 2006-05-27
All you have to do is paste the everything over your /usr directory. (That's if you downloaded a .tar.gz) I'm stuck at:

harold@ubuntu:/usr/lib$ aim
aim: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

I read [here]("http://lists.debian.org/debian-user/2002/03/msg01671.html") that you had to copy a file and paste iot as a different one, but the version in the repos is different, now.

---

### Post by stanz on 2006-05-27
[quote=Harold P]All you have to do is paste the everything over your /usr directory. (That's if you downloaded a .tar.gz)[/quote]
I did not notice a tar.gz. I tried for the deb- first.
> I'm stuck at:
harold@ubuntu:/usr/lib$ aim
aim: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
Did you notice- i've got that same message!?
> I read [here]("http://lists.debian.org/debian-user/2002/03/msg01671.html") that you had to copy a file and paste iot as a different one, but the version in the repos is different, now.
For some reason- their copying files...or linking them.
I'm no pro here, but i still think- files need to be put in their respective folders, to work 'with a linux box'.
I submitted a report, thats on their page...i ask everyone to do the same.
When they ask for 'steps to repeat'... I typed in...
learn linux & get ubuntu !!
Thx for your reply...I'm wondering if aim is worth this trouble~
I wanted voice & cam...otherwise Gaim is good.

---

