---
title: "Please help quick"
date: 2006-05-12
forum: General Help
---

### Post by Masterminds on 2006-05-12
Well I don't know if its because im new to Ubuntu or f iim just a n00b.
BUT i tried to install my modem driver (tiscali) so i could access the internet,
BUT it does auto run or boot at all.
i accessed files on the disc such as setup ect but no luck.
and it doesn't say anything on the disc case about not working on linux or anything.
can someone please tell me whats wrong???
oh yeah and if your wondering how i am on the internet here, its a different computer.
(running windows :( )

---

### Post by Masterminds on 2006-05-12
well can someone please help me because i am seriously thinking of changing back to windows until i find somthing that will work.

oh yes and the connectioon is via USB not ethernet

---

### Post by christhemonkey on 2006-05-12
On tiscali?

Are you using the ADSL modemy thing they send you?
Sagem F@ST 800-840?

---

### Post by Masterminds on 2006-05-12
no mines a thomson speedtouch 330
which is what they sent me

---

### Post by christhemonkey on 2006-05-12
Ah. [This one?]("http://www.dsl-warehouse.co.uk/product.asp?pr=ST330")

[This site]("http://nyati-buffaloblog.blogspot.com/2006/04/ubuntu-speedtouch-howto.html") seems perfect for what you need to do

---

### Post by Masterminds on 2006-05-12
ok thanks alot mate. i'll try that.

---

### Post by christhemonkey on 2006-05-12
S'awight!

---

### Post by Masterminds on 2006-05-12
it says somthing like does not surrport archieve on there when i try to open the files??? can anyone help???
(they are .deb i think)

---

### Post by Masterminds on 2006-05-12
can you tell me how to install that debian thing because i read how to change the settings to universe but there are about 5 options that have a universe tag.

---

### Post by meng on 2006-05-12
[QUOTE=Masterminds]can you tell me how to install that debian thing because i read how to change the settings to universe but there are about 5 options that have a universe tag.[/QUOTE]
Not sure if I understand the question. If you mean how to install using a .deb file you've already downloaded then drop down to the CLI and enter:
sudo dpkg -i *(name of the file)*.deb

---

### Post by Masterminds on 2006-05-12
when ever i try to open a .deb file it says "Archive type not supported"

---

### Post by dsokus on 2006-05-12
[QUOTE=Masterminds]when ever i try to open a .deb file it says "Archive type not supported"[/QUOTE]
I have that too, actually!! :-k 

My solution has been to simply use the Synaptic Package Manager for anything I want to install, but then I do realize it probably doesn't work for you in this case. :( 

Once you get it to work, please make sure you post what you did to fix it..!

---

### Post by Masterminds on 2006-05-12
I tried adding Debian in the add application option but it says i need somthing to do with universe.
and i thikn i need to connect to the internet to add this app. but i need it to get on the internet!!

is there anyway without going on the internet???

---

### Post by Masterminds on 2006-05-12
-bump-

---

### Post by meng on 2006-05-12
[QUOTE=meng]Not sure if I understand the question. If you mean how to install using a .deb file you've already downloaded then drop down to the CLI and enter:
sudo dpkg -i *(name of the file)*.deb[/QUOTE]
^^^^^^^
Sorry, I'm still confused. Do you have the .deb file or not? And if you do, have you tried dpkg?

---

### Post by Masterminds on 2006-05-12
well i have only installed Ubuntu yesterday.
i have a .deb file but not the software to use it. i dont know what dpkg is :)

---

### Post by meng on 2006-05-12
If you have the .deb file then you don't need to get it from the repositories, which as you pointed out you can't do anyway.

So the next question is: have you gone to the command prompt and typed:
**sudo dpkg -i *(name of the file)*.deb**

If so, what happened?
If not, why not?

---

### Post by Masterminds on 2006-05-12
i am new to ubuntu and new to linux. the only experience i have had is from live CD's
thats why not :) i will try it. thanks mate

---

### Post by meng on 2006-05-12
Best of luck. Suggest next time you read answers before bumping. For my part, I'll strive to write more clearly in future.

---

### Post by Masterminds on 2006-05-12
well i tried but no luck.
says somthing about and error.
i tried again and it says file does not exist. i typed it in correct aswell

---

### Post by meng on 2006-05-12
Can you tell me where this .deb file is located? You need to be in the same directory (or else type the full path to the location).

---

### Post by Masterminds on 2006-05-12
well it was on my pendrive but its on my desktop.
and how can i get the whole path??
on windows it shows it in the address bar but there isnt one on ubuntu (that i can see)

---

### Post by Masterminds on 2006-05-12
or did you mean which website

---

### Post by meng on 2006-05-12
Try this then:

**cd ~/Desktop**
**sudo dpkg -i *(name of deb)*.deb**

---

### Post by christhemonkey on 2006-05-12
```
cd /location/of/file/
sudo dpkg -i first-few-letters-of-file-then-press-TAB 
```
Obviously replacing first-few-letters-of-file with the first letters of the file and directory of file with where you copied it to.

Then note any error output and report back here!

---

### Post by Masterminds on 2006-05-12
ok thanks alot mate. its working

---

### Post by Masterminds on 2006-05-13
ok well one of the files worked and it was only an up date.
the one i need to get on the net is a new install.
do i need to put somthing different in for a new install???

---

### Post by Masterminds on 2006-05-13
-bump-

---

### Post by christhemonkey on 2006-05-13
no.
just type
```
cd /where/it/is
sudo dpkg -i whatever.deb
```
into a terminal.

---

### Post by Masterminds on 2006-05-13
well that doesnt work.
well i give up. i will change to windows again till i find away to do this on ubutu or on a different version of linux :(

---

### Post by christhemonkey on 2006-05-13
Fair enough, but if you dont mind me asking, what error did it give?

Or what more precisely didnt work?

---

### Post by Masterminds on 2006-05-13
its not that.
i just cant get a driver to install so i can access the internet through my USB modem.

---

### Post by christhemonkey on 2006-05-13
I mean where along the way did you get stuck?

Did you finish the instructions [here]("http://nyati-buffaloblog.blogspot.com/2006/04/ubuntu-speedtouch-howto.html") and it not work?

Or did the installing of the firmware and stuff fail?


Or did you just get fed up of having to type things into a terminal? :p

---

### Post by Masterminds on 2006-05-13
the first download thing of that sit installed fine.
then when it came to the driver,
i typed the command in and then my password then the loading thing came up like on the first one but then nothing happend.
the install didnt come up or anything

---

### Post by christhemonkey on 2006-05-13
Did you try again?

Sometimes these things are randomly arkward!

Anyways hope you figure your problem out, if your still stuck i shall help again tommorow
I am going to bed now!

Good night

---

### Post by meng on 2006-05-13
Masterminds,
It would help if you were specific about what you're trying to do, what you actually did and the error message/s you got. There are lots of experienced people (not me) around who can help you, but they're not going to try to read your mind.

---

### Post by Masterminds on 2006-05-27
no error message comes up,
it just doesnt install the program i want

---

### Post by meng on 2006-05-27
When you "sudo dpkg -i [etc]", something must come up. If not an error message, then some sort of confirmatory message. Based on what you told us, we can't be sure what's happening. Also, just because you installed one package or driver, doesn't necessarily mean that everything is done. There may be other packages required, or else you may need to configure some settings for the connection.

Again, I know I'm repeating myself, but it's much harder to offer help if you can't give us details. Feel free to cut and paste the terminal output, as many others do here.

---

### Post by sadjack on 2006-05-28
I know it does not help you setup your modem, but my experience with the usb ones supplied by tiscali is crap. I ended up buying a modem/router and connected to that via the ethernet port.

I don't mind giving things a fair try but sometimes life is too short to spend it trying to get stuff to work that was designed for windows anyway.

Hope you get it sorted.

---

### Post by 3rdalbum on 2006-05-28
Masterminds: On Linux, you don't generally get a "Setup program" like you do on Windows. If you typed in the "sudo dpkg -i" stuff, and it didn't display an error message, then the software is now INSTALLED.

If there are instructions that come with the driver about how to configure it, you should follow these now.

---

