---
title: "Smartboard Software for Linux Help Please!"
date: 2010-10-19
forum: General Help
---

### Post by sarsar on 2010-10-19
Hello,

Im an absolute beginner at Ubuntu so i will probably need a lot of help doing something that is probably very simple. I am currently training to be a teacher and so i have downloaded some SMART Board Software. SMART (the company who produce the software) have sent me the Linux version of their software complete with the drivers. However, when i went to open the download the message came up with: 

Could not open the file /home/[my name]/.cache/.fr-…e With Drivers 10.package using the Unicode (UTF- character encoding.

I have selected both options in the menu but it keeps coming up with this message. 

Please could somebody help me? Is there another way of opening this package and a kind of coding that i don't know about? or do i have to open it in the terminal? if so please could someone tell me how. 

Btw: Im using Ubuntu 10.04 LTS. If you need any more info i will try and give you it. 


Many Thanks 

Sarsar

---

### Post by nothingspecial on 2010-10-19
First, don`t worry, it does work. My wife is also a trainee teacher and we sorted it out.......


......trouble is, it was over a year a go and I can`t remember how.

Where is the downloaded stuff? Your home folder, your Desktop, Downloads or in .cache?

If I can look at what is on your computer, I hope I will remember.

---

### Post by sarsar on 2010-10-19
Thankyou, i have seen people who are able to do it, the person whose review i read said it came right out of the box and worked. I think they knew what they were doing though. 

Ok, i downloaded it and it automatically saved to my .cache, it is literally straight from download, ie: you download it and it opens up. I cannot get it to save onto my desktop or a documents folder, in fact the save option is completely greyed out [unclickable]. It looks like you cannot even open the file.  

I think i have managed to get you a print screen thing. 

Thankyou

---

### Post by nothingspecial on 2010-10-19
Post the output of ```
ls -la .cache | grep Drivers
``` Please.

Ie open a terminal and type that, then copy what it says back here. And please put code tags around it ------ select all the text you paste then click the # near the right of the toolbar, just next to the <>, in the box that you post replies in, if you see what I mean.

---

### Post by sarsar on 2010-10-19
```
ls: cannot access Drivers: No such file or directory
.cache:
total 72
drwx------ 10 sarsar sarsar  4096 2010-10-19 21:11 .
drwxr-xr-x 41 sarsar sarsar  4096 2010-10-19 22:21 ..
drwxr-xr-x  3 sarsar sarsar  4096 2010-08-18 20:58 checkbox
-rw-r--r--  1 sarsar sarsar 16384 2010-10-19 22:10 event-sound-cache.tdb.52e4b7b3a097bdccc9d2756f4c5c6673.i486-pc-linux-gnu
drwx------  3 sarsar sarsar  4096 2010-10-19 21:10 .fr-1BySAX
drwx------  3 sarsar sarsar  4096 2010-10-19 21:11 .fr-7cFoFQ
drwx------  3 sarsar sarsar  4096 2010-10-17 20:00 google-chrome
-rw-r--r--  1 sarsar sarsar   617 2010-10-19 22:23 indicator-applet.log
-rw-r--r--  1 sarsar sarsar  4137 2010-10-19 22:22 indicator-applet-session.log
drwx------  3 sarsar sarsar  4096 2010-09-05 21:37 indicators
-rw-r--r--  1 sarsar sarsar   228 2010-10-19 21:13 notify-osd.log
drwx------  4 sarsar sarsar  4096 2010-09-05 14:47 rhythmbox
drwxr-xr-x  2 sarsar sarsar  4096 2010-08-06 23:42 update-manager-core
drwx------  2 sarsar sarsar  4096 2010-08-30 22:21 wallpaper
```

Thats what came up. Hope thats right

---

### Post by nothingspecial on 2010-10-19
> **sarsar said:**
> ```
ls: cannot access Drivers: No such file or directory
.cache:
total 72
drwx------ 10 sarsar sarsar  4096 2010-10-19 21:11 .
drwxr-xr-x 41 sarsar sarsar  4096 2010-10-19 22:21 ..
drwxr-xr-x  3 sarsar sarsar  4096 2010-08-18 20:58 checkbox
-rw-r--r--  1 sarsar sarsar 16384 2010-10-19 22:10 event-sound-cache.tdb.52e4b7b3a097bdccc9d2756f4c5c6673.i486-pc-linux-gnu
drwx------  3 sarsar sarsar  4096 2010-10-19 21:10 .fr-1BySAX
drwx------  3 sarsar sarsar  4096 2010-10-19 21:11 .fr-7cFoFQ
drwx------  3 sarsar sarsar  4096 2010-10-17 20:00 google-chrome
-rw-r--r--  1 sarsar sarsar   617 2010-10-19 22:23 indicator-applet.log
-rw-r--r--  1 sarsar sarsar  4137 2010-10-19 22:22 indicator-applet-session.log
drwx------  3 sarsar sarsar  4096 2010-09-05 21:37 indicators
-rw-r--r--  1 sarsar sarsar   228 2010-10-19 21:13 notify-osd.log
drwx------  4 sarsar sarsar  4096 2010-09-05 14:47 rhythmbox
drwxr-xr-x  2 sarsar sarsar  4096 2010-08-06 23:42 update-manager-core
drwx------  2 sarsar sarsar  4096 2010-08-30 22:21 wallpaper
```Thats what came up. Hope thats right

It`s not what I was looking for, but that doesn`t matter. I`ve remebered. You need the autopackage installation system. I`m just looking in to how to get it now.

---

### Post by sarsar on 2010-10-19
Sorry about that, i thought that was what you needed as that was what came up when i pasted it in. 

Thankyou for looking what i will need. Hopefully we might have a Smartboard activity on Thursday thanks to you.

---

### Post by sarsar on 2010-10-19
My computer has just caught up with itself and come up with some more info, thats probably what you were looking for as it said that the program 'total' was not installed and then lots of lovely figures and program names as well as some suggestions.

---

### Post by nothingspecial on 2010-10-19
If I remember correctly, you need an installer called autopackage that doesn`t come with ubuntu. I am trying to find it. Hold tight. :)

---

### Post by nothingspecial on 2010-10-19
Right, this is annoying - not you :)

I cannot find a download of the autopackage software.

All is not lost however. I notice, relooking at your screenshot, that the download is in ~/.cache/.fr-1BySAX/

I have to go now, sorry but this does work. I will check back, but it may 10 hours or more.

In the mean time, contact smartbook support, although I don`t hold out much hope. We will get this working though. :)

And, who knows, a smartbook expert may chime in soon.

---

### Post by sarsar on 2010-10-19
Hey Thankyou so much for your support the past hour, it means alot that people are willing to help me with such a strange request. 

Hopefully we will get to the bottom of this. I really hope so anyway, im not giving up, that means using windows *shivers*.

---

### Post by [::AP::] on 2010-10-19
Greetings - 

I cannot provide any help, but wish you best of luck. 

Additionally, I hope you do not find this post as irrelevant/annoying...

You are learning how to use Smartboards?
I am sure that you will find that future students of yours will find them cool/engaging. Our school district installed Smartboards/ Promethean boards in 2007 when I was in 6th grade  - I cannot imagine a class without them! Our teachers use them every minute of everyday, and I have found that they make learning/teaching fun, engaging, and much easier. The only downside is when there is the (rare) malfunction (bulb goes out, etc), teachers seem unable to conduct class. They have become so dependent on these wonderful tools, that they seem to forget that just a couple years ago they were using old projectors or the chalk/white boards. :/

Ahh well, 

Best of Luck!
Good luck in your future teaching!

[::AP::]

---

### Post by nothingspecial on 2010-10-20
Ok, lets see if we can get to the files you downloaded

```
ls -la ~/.cache/.fr-1BySAX/
```

---

### Post by nothingspecial on 2010-10-20
By the way, have you just downloaded the 30 day trial version in order to complete an asignment of have you paid for the full version.

---

### Post by sarsar on 2010-10-20
My uni have paid for me to use it so Im hopefully getting the full version - when i get to it. 

Ive managed to find someone who can solve this problem at my uni (well he thinks he can) apparently we don't need autopackage [if we cant find it] as it has been packaged up using auto package. The file is a tar.gz file. It has been compressed and needs uncompressing. Does anyone know how to open one of these files? The IT guy said something about manually installing the file. 

To AP: Don't worry I will not have a breakdown if my smartboard breaks down. I was brought up in a time when there was no smartboards and whiteboards were a new thing- I know I'm ancient lol!

i did not find you comment distracting or annoying, its nice to know how people actually experiencing education feel about teaching. I'm glad they make the lesson engaging. If you want to say anything else about Interactive boards and your experiences feel free, its extremely interesting as i sometimes feel they are very tokenistic- using them for the sake of using them rather than for a purpose to extend learning, rather than actually doing activities.

Anyway that is beyond the post. 

In reply to the code given to me by nothing special
It has come up with


ls -la ~/.cache/.fr-1BySAX/
ls: cannot access /home/sarsar/.cache/.fr-1BySAX/: No such file or directory

I will try and get up what i had earlier with the I.T guy as this was much more useful and may help you more. 

Thankyou all 

Sarsar

---

### Post by nothingspecial on 2010-10-20
> **sarsar said:**
>  The file is a tar.gz file. It has been compressed and needs uncompressing. Does anyone know how to open one of these files?


You can normally uncompress a .tar.gz file by double clicking it, but that`s not the point.

Once it is uncompressed, you have to manually install it. I just need to know where, exactly it is.

Can you find the file with your places menu?

---

### Post by sarsar on 2010-10-20
Right, i have installed it on my desktop. I have done a bit of a print screen and highlighted it so you will be able to see it. No idea if it helps. 

How do i know what the file name is?

Just earlier we did tar -zxvf <filename> ./smart\ notebook\software\with\drivers\10.package 

and it brought up lots of information that gives details on the program and how it was packaged. Problem is i dont know what the file name would be if ive saved it. 

Thankyou

Sarsar

---

### Post by nothingspecial on 2010-10-20
I can see the tar.gz package, but where did you extract it to?

I`m guessing the 6 other files/directories on your desktop are other things. 

If they are, do it again 
```

tar -zxvf ~/Desktop/smart\ notebook\software\with\drivers\10.package 
```

if not, which are the extracted files?

And please tell me, are you running Ubuntu or lubuntu, the commands will work the same but the clicking stuff will not, if you see what I mean.

---

### Post by sarsar on 2010-10-20
Dont know if this is any help, BUT this is the properties of the software. May shed a bit of light to the more knowledgeable :confused:

---

### Post by nothingspecial on 2010-10-20
```
tar -zxvf ~/Desktop/smart\ notebook\software\with\drivers\10.package
```


again

---

### Post by sarsar on 2010-10-20
Brilliant!!!!!! SUCESS- I think!!!
Ive extracted it and put in that command and all of a sudden, BINGO its started reading it, im going to put the print screens up just to make sure but i think weve progressed.

By the way, im using Ubuntu 10.04 hope that clears things up a bit


Thanks

Sarsar

---

### Post by sarsar on 2010-10-20
This is what came up. Im going to imput yes in a moment. I will keep posting as i progress.

---

### Post by sarsar on 2010-10-20
Auto Package is now installing!!! Hopefully this will be the end of this!!!

Will keep updating. 

Thankyou for your help so far

---

### Post by nothingspecial on 2010-10-20
Keep going :)

---

### Post by sarsar on 2010-10-20
Its installing it all now. 

THANKYOU SO MUCH, IM SO GRATEFUL for ALL of your help and patience with this!!!!! I think we have cracked it!! 

My class will be so happy tomorrow!!

---

### Post by nothingspecial on 2010-10-20
Have you got it?

Definitely?

---

### Post by sarsar on 2010-10-20
Its currently unpacking everything at the moment, I think i have got it as its all there. 

It isn't desperate for tomorrow, mainly after half term, about a week and half away. 

If i have any other problems i will repost asking for help again, but for now i think were away. 

Thanks again for all the help

Sarsar

---

### Post by nothingspecial on 2010-10-20
;) :guitar:

---

### Post by sarsar on 2010-10-20
GOT IT!!! 

WE ARE OFFICIALLY AWAY!!!

Thankyou

---

### Post by la cónica on 2010-12-26
hi! I'm also trying to install Smart software on Ubuntu 10.04, without any success so far. When I try to open the downloaded file after extracting it, without the Autopackage software, it creates a folder named autopackage with a 6-digit number, but after a few seconds, the folder disappears and nothing happens. When I try with the command package install or with the Autopackage software, it claims that I should install it with su privileges, and even if I do super user, it still asks for a super user installer...

I don't know what to do.

Thanks for any hint you may provide.

---

### Post by Sallée on 2012-05-08
Run it like it is a shell (modified for drivers package):
```
sudo chmod 500 SMART\ Product\ Drivers\ 10.package
sudo ./SMART\ Product\ Drivers\ 10.package
```
Then it should install autopackage so you can run the following, if necessary:
```
sudo package install SMART\ Product\ Drivers\ 10.package 
``` 
There is another dependency issue that arises, so I would seek out the .deb from SMART.  

On related note, though, I am not getting touch recognition.  Can anyone offer assistance on this old thread?

---

### Post by digitography on 2012-06-08
sorry to open this can of worms again.
I too am trying to install the smartboard software on Ubuntu 11.04.

what I get is nothing like what was described in this thread.

I can download the tar file and extract it using archive manager, so I have a folder called 
smartboard103 with the extracted files.

I see no auto install, or anything like that.
the read me file reads like a foreign language, I have never seen anything like it.
If anyone can help it would be appreciated.

---

### Post by Sallée on 2012-06-08
There should be a .package file.  Run that like any other script (./smartwhatever.package).  It should then download the auto package files and thereafter you can use the commands listed in the readme.

---

### Post by oldos2er on 2012-06-09
Old thread closed. If anyone's still having problems, please start a new thread.

---

