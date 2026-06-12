---
title: "Massively complicated problems that are probably to advanced for you but I need help"
date: 2011-09-06
forum: General Help
---

### Post by I-Like-Pie on 2011-09-06
Massively complicated problems that are probably to advanced for you but I need help
 

 I do not have ubuntu installed right now on my computer
 

 I have windows installed right now on my computer
 

 I have ubuntu 10.10 on a dvd and 11.04 on an usb stick both are 64 bit version
 

 To run ubuntu 10.10 from the dvd on my computer I need to select the noapic option by entering the dvd into the computer wait for it to boot when the keyboard shows up press f6 then when the menu shows up select try ubuntu and press f6 and select the noapic option
 

 NOW
 

 When I plug in the usb stick and boot from the stick I cant see or figure out how to find the noapic option and just trying to boot from the stick normally freezes the computer just like not selecting the noapic option from the dvd
 

 SO
 

 Answer any question you know the answer to, there is no need for 1 person to answer them all
 

 Question 1
 

 How do I select the noapic option for ubuntu 11.04 from an usb stick if at all possible
 

 Question 2
 

 If it is possible to install unbuntu 11.04 with the noapic option how do I make it so that when Ubuntu 11.04 launches it automatically launches with the noapic option
 

 Question 3
 
In ubuntu 10.10 if it is installed how do I make it so that every time it starts up it starts with the noapic option automatically already preselected
 

 Question 4

If I have ubuntu 10.10 installed on my computer the 64 bit version and lets say it automatically boots with the noapic option preselected is it possible to upgrade by selecting upgrade from within the system and having ubuntu 11.04 function also with the noapic option?

---

### Post by IWantFroyo on 2011-09-06
On 10.10, to have it automatically boot with noapic, do this.
```
sudo gedit /etc/default/grub
```

You'll see a line that says this:
GRUB_CMDLINE_LINUX=""

Put:
```
noapic
```
In between the "s.

Then, run:
```
sudo update-grub
```

---

### Post by I-Like-Pie on 2011-09-06
There is a problem, after installing 10.10 the program wanted me to restart so I did and now ubuntu wont boot and when I press f6 whilst booting the grub flashes for 1 sec tops and then starts anyway and I cant select anything and it simply freezes

SO 

How do I from the boot menu select anything and make it boot with the noapic option

---

### Post by IWantFroyo on 2011-09-06
Press 'e' once you get into Grub, and then add noapic to the end.

Edit- There are better places to add noapic, but the end will do, in a pinch. I don't remember the right place.

---

### Post by I-Like-Pie on 2011-09-06
I Fixed that specific problem

I was able to access the grub which only flashed by for one second by pressing f2 as soon as the computer starts then selecting exit without saving that brought me up to the grub, then I edited the first option by adding the word noapic after the word "quite splash" I added a spacebar hit as well after the words "quite splash"

Now I am in Ubuntu 10.10 lets see if the code change works

---

### Post by I-Like-Pie on 2011-09-06
The code changes work :)

But I made some changes to your instructions.

After opening the terminal and writing sudo gedit /etc/default/grub and entering noapic inbetween the 2 "

 I pressed save and closed the window

Then I wrote sudo update-grub in the terminal

And it worked wish is nice

Now only 3 questions remain but they are probably to complicated for the Ubuntu community to answer :)

---

### Post by haqking on 2011-09-06
> **I-Like-Pie said:**
> 


After opening the terminal and writing **sudo gedit** /etc/default/grub and entering noapic inbetween the 2 "


Now only 3 questions remain but they are probably to complicated for the Ubuntu community to answer :)

Dissing or belittling the knowledge of the community is not the best way to get assistance.

And gedit is graphical and so you should you use gksudo and not sudo

---

### Post by Iowan on 2011-09-06
> **I-Like-Pie said:**
> ... then I edited the first option by adding the word noapic after the word "quite splash" I added a spacebar hit as well after the words "quite splash"I thought it was "quiet splash"
> **I-Like-Pie said:**
> 
Now only 3 questions remain but they are probably [COLOR="Red"]too[/COLOR] complicated for the Ubuntu community to answer :)
We won't know unless you ask... ;)

---

### Post by WorMzy on 2011-09-06
> **Iowan said:**
> We won't know unless you ask... ;)

Indeed. There are a significant number of users on these forums with enough experience to answer the vast majority of "complicated" questions. Try us and see.

---

### Post by haqking on 2011-09-06
> **Iowan said:**
> I thought it was "quiet splash"

We won't know unless you ask... ;)

> **WorMzy said:**
> Indeed. There are a significant number of users on these forums with enough experience to answer the vast majority of "complicated" questions. Try us and see.

his 4 questions are in the OP.

I was put off by the thread title and the comment about community not being able to answer.

so i am gonna sulk in another thread ;-)

---

### Post by Dangertux on 2011-09-06
I have the answers to your questions, but they are probably too advanced for you to use.

Not to be condescending, but name your next thread better if you want help imo.

P.S : it's noacpi and quiet splash.

---

### Post by WorMzy on 2011-09-06
> **haqking said:**
> his 4 questions are in the OP.

I was put off by the thread title and the comment about community not being able to answer.

so i am gonna sulk in another thread ;-)

Oh. I understood that to mean s/he has a further three questions.

As far as I can tell, questions two and three have already been answered.

My answer to question 1 is difficult to articulate, and may not be accurate any more. But in my experience, you need to press and hold *any* key between the initial boot message (booting from USB), and when screen turns purple, then you'll be presented with the "old school" locale/keymap selection screen, which lets you select several different boot options by pressing one of the F# keys. I can't really be more specific than that, it's been years since I've done it myself.

As for question 4: so long as you've declared noacpi (which is what I assume the OP means by "noapic") in the GRUB_CMDLINE_LINUX_DEFAULT array variable, /etc/default/grub and the file itself isn't replaced during the upgrade, grub.cfg should be generated with the correct boot options.

---

### Post by I-Like-Pie on 2011-09-06
The screen does not turn purple on the usb 11.04 version it is black and white it is not pruble but black and white and there is not keybaord sign when entering the menu it just happens like wham and you are there and it is black and white

Questions 1 2 and 4 remain unanswered atleast for me

And it was correct to write that it was way too complicated because no one has given a step by step answer on hot to do it so far and it triggered several responses :)

---

### Post by Dangertux on 2011-09-06
> **I-Like-Pie said:**
> The screen does not turn purple on the usb 11.04 version it is black and white it is not pruble but black and white and there is not keybaord sign when entering the menu it just happens like wham and you are there and it is black and white

Questions 1 2 and 4 remain unanswered atleast for me

And it was correct to write that it was way too complicated because no one has given a step by step answer on hot to do it so far and it triggered several responses :)

Here's your step by step guide.

[http://www.gnu.org/software/grub/grub-documentation.en.html](http://www.gnu.org/software/grub/grub-documentation.en.html)

---

### Post by linuxuser12345 on 2011-09-06
Have you tried downloading and installing Ubuntu 10.04.3, instead? One version of Ubuntu will sometimes act differently on a machine than another version of Ubuntu.

---

### Post by I-Like-Pie on 2011-09-06
> **Dangertux said:**
> Here's your step by step guide.

[http://www.gnu.org/software/grub/grub-documentation.en.html](http://www.gnu.org/software/grub/grub-documentation.en.html)


I dont understand anything

I was thinking more of a guide in the way off

Click butto X then type in words XXXXX and then it will work

---

### Post by I-Like-Pie on 2011-09-06
> **linuxuser12345 said:**
> Have you tried downloading and installing Ubuntu 10.04.3, instead? One version of Ubuntu will sometimes act differently on a machine than another version of Ubuntu.


You are asking about 11.04 right now 10.04

And right now At this second i am in ubuntu 10.10 which is working and that is nice

If you are saying I should click system --- administration --- update maanger and then click the upgrade button to version 11.04 then the answer is no i havent tried that

---

### Post by Iowan on 2011-09-06
> **haqking said:**
> his 4 questions are in the OP.Sorry - missed it... I'm in an odd mood tonight. Which questions remain unanswered?
I've upgraded with some luck, but a fresh install is usually recommended.

---

### Post by I-Like-Pie on 2011-09-06
> **Iowan said:**
> Sorry - missed it... I'm in an odd mood tonight. Which questions remain unanswered?
I've upgraded with some luck, but a fresh install is usually recommended.


Question 1, 2 ,4 :)

---

### Post by drs305 on 2011-09-06
Adding the kernel switch to the 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
line of /etc/default/grub and then running "sudo update-grub" will make any option you place on that line permanent.

When you do an online upgrade (say from 10.10 to 11.04), as grub updates it will ask if you want to keep the existing files or upgrade. You can let it upgrade the files but at some point you will be asked if you want to add any kernel options. At that point, you would type in the kernel options you desire, then TAB to OK and press ENTER to continue the Grub 2 upgrade.

If you need to use the nomodeset when booting the LiveCD, you can press F6 as the CD starts booting to allow you to add kernel options. Here is a community doc I created a while back which explans how do this, should you need to use it:
[https://help.ubuntu.com/community/LiveCDBootOptions]("https://help.ubuntu.com/community/LiveCDBootOptions")

---

### Post by I-Like-Pie on 2011-09-06
> **drs305 said:**
> Adding the kernel switch to the 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
line of /etc/default/grub and then running "sudo update-grub" will make any option you place on that line permanent.

When you do an online upgrade (say from 10.10 to 11.04), as grub updates it will ask if you want to keep the existing files or upgrade. You can let it upgrade the files but at some point you will be asked if you want to add any kernel options. At that point, you would type in the kernel options you desire, then TAB to OK and press ENTER to continue the Grub 2 upgrade.

If you need to use the nomodeset when booting the LiveCD, you can press F6 as the CD starts booting to allow you to add kernel options. Here is a community doc I created a while back which explans how do this, should you need to use it:
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)


Question 3 has been answered

AND

The main point in question 1 is that there is NO f6 option when using the usb stick 11.04 version i can press tab and get some weired code line at the bottom and that is all

I do not, I say again do not get a pop out square window like in version 10.10 when i press f6 or any f button and pressing E does nothing

---

### Post by overdrank on 2011-09-06
Some post have been removed. Please keep the [Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy") in mind when responding.
> The purpose of the Ubuntu Forums is to provide support for Ubuntu. We also want this to be a place where community can develop and we can enjoy one another's company. To achieve this, we strive to maintain an atmosphere that can be enjoyed by all and we ask all members of the community to be respectful at all times. This means please use etiquette and politeness. Treat people with kindness, gentleness and respect. If you do this, the rest of the code of conduct won't need more than a cursory mention.
Thanks

---

