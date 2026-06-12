---
title: "administrator chiled (root pass)"
date: 2011-11-07
forum: General Help
---

### Post by sonja4flash on 2011-11-07
Did try everything, all /to me/ available  tips to change admin pass what means gnome / edit: GRUB access/ (retyped passwd don&#8217;t match)- sudo access (am I root/ enabled/disabled root pass/?)- Anyhow- problem did appear after someone brake into my mail address long time ago- but in 6 month with Ubuntu with no Administration possibility feel like someone else control my life, and I hate it. 
Can anyone help?

---

### Post by haqking on 2011-11-07
> **sonja4flash said:**
> Did try everything, all /to me/ available  tips to change admin pass what means gnome access (passwd dont match in two tipping )- sudo access (am I root/ enabled/disabled root pass/?)- Anihow- problem did apear after someone brake into my mail address long time ago- but in 6 month with Ubuntu with no Administration possibility feel like someone else control my life, and I hate it. 
Can anyone help?

I dont understand any of that, but i think you mean you need to reset your admin password ?

So here is a link

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by sonja4flash on 2011-11-07
in steed - i did try all available informations I’m mentioning Gnom- should wrote GRUB-  Is not working!
But tnx anyhow.

---

### Post by haqking on 2011-11-07
> **sonja4flash said:**
> in steed - i did try all available informations I’m mentioning Gnom- should wrote GRUB-  Is not working!
But tnx anyhow.

you mean grub is not working ?

in what way ?

you boot to a grub prompt ?

no grub menu ?

error message ?

---

### Post by sonja4flash on 2011-11-07
available  tips to change admin pass what means gnome / edit: GRUB access/ (retyped passwd don&#8217;t match)
Did done everything- now should write new passwd- and password- don&#8217;t match-

---

### Post by haqking on 2011-11-07
> **sonja4flash said:**
> available  tips to change admin pass what means gnome / edit: GRUB access/ (retyped passwd don’t match)

I am totally lost as to what you are saying i am afraid.

I already give you a link to change your admin password.

---

### Post by sonja4flash on 2011-11-07
OK- In that link i did get to step

> Your password is still being accepted. Just type the password and hit *Enter* when you're done. You'll be prompted to retype the password. Do so and hit *Enter* again.  Now the password should be reset. Type 
exit


I cont tipe nothing- because Is not working. For me it seams as serous problem- so did try all different ways in retyping lines- in sted /ro /rw or other way around- did tray in sudo- as I did mention- I need help.
Only thing what i didn’t try- and is offer on UBUNTU community as help is changing pass using E UBUNTU- i don’t have CD with ubuntu- and if i have cont use CD cause im not administrator.

---

### Post by haqking on 2011-11-07
> **sonja4flash said:**
> OK- In that link i did get to step



I cont tipe nothing- because Is not working. For me it seams as serous problem- so did try all different ways in retyping lines- in sted /ro /rw or other way around- did tray in sudo- as I did mention- I need help.
Only thing what i didn’t try- and is offer on UBUNTU community as help is changing pass using E UBUNTU- i don’t have CD with ubuntu- and if i have cont use CD cause im not administrator.

I really cant understand what you are saying.

When you say you cant type nothing ? if you mean your passward, it does not show on the screen when you type it.

Just type the password as you usually would (nothing will show on the screen) then press enter

---

### Post by sonja4flash on 2011-11-07
Here is link if someone else have same problems- is not working for me- but at least brings hope something will be done. 
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by haqking on 2011-11-07
> **sonja4flash said:**
> Here is link if someone else have same problems- is not working for me- but at least brings hope something will be done. 
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

it does work, it is the same method as link i posted above.

When typing the password nothing will show on the screen, just type it and press enter

---

### Post by sonja4flash on 2011-11-07
On that link I get to> 
Then follow the steps 6-8 as mentioned above. 
Is not working. Cont type nothing cause retyped pass don’t match- no meter do I see it or not.

Had to shot down my computer by violence. And be in hope I didn’t dameg nothing- so will build up it system again.

---

### Post by sonja4flash on 2011-11-07
When I wrote pass for first time- i think- that&#8217;s it
When I retype pass- im in fier- but it doesn&#8217;t match to first one
i try third or second time, and fort time- all those times pass don&#8217;t match- then I&#8217;m upset cause I cont do nothing any more except  
step i did mention above- Shot down by violence. 
(can I call that reboot?)

---

### Post by sonja4flash on 2011-11-07
This are tips that someone did wrote on my mother thong in year  2008/ 2009 when my Linux problems start to develop- (and that happen in synchronisation with life with  Debian developers: what doesnt mean I know anything about programming) 


Boot Linux frome Live CD
Mount your partition where is your Ubuntu.

1.Way

Change fail /etc/shadow on that partition (NOTE: not /etc/shaddow on LiveCD but file on other partition)
[I]in /etc/ shadow file are codes of all users- of course codes are hash shape. Here is one from shadow file
[/I]```
root:$1$acjK13Jkd&kHamJdUOxxx#5:13000:0:99999:7::::
```It meand what is important, is important in first row (rows are seperatet with ```
:
``` * two dots (like i will show now*) :) end of quote  
what i make as symbol ```
 )
``` [I]AND WE ALL SEE SMILE 
 Im translating tips on most famous magasine for computer problems called BUG[/I] 

 here is username- in second roe is hash passwd -. you have to delet second row. On that way you delet paswd from user
what meand root user would look like this
```
root::13000:0:99999:7::::
```U do same for your user 

2.way 
chydr your self in old partition 
Change  /dev/sda3 with partition where is Ubuntu 
```
mkdir -p /media/old
mount /dev/sda3 /media/old
mount --bind /dev /media/old/dev
mount -t sysfs none /media/sys
mount -t proc none /media/proc
chroot /media/old
```Naw you set new root pass
In this exapmel user will be svabo
```


passwd root
#type new pass for root

passwd svabo
#type new pass for svabo
```If you dont know what was your username you can do as this
```
useradd -md /home/svabo -p 'password' svabo
```after you did all changes you  have to do this
```

exit
 umount /media/old/dev
 umount /media/old/proc
 umount /media/old/sys
 umount /media/old
 ls -a /media/old # chack is it empty

 rm -R /media/old # NOTE: this run just if uper order dont write nothing

 reboot # this will restart your system.
```

After this is done in aria in which is my native- is more posibelety will reset my pass by using soft disk- than anything else (something to do with NGO activisam- and monopol whas befor I turn to UBUNTU.

---

### Post by sonja4flash on 2011-11-07
Was thinking noone wont get me seriously - only thing what I can do now is- what - turn on windows again- that I could continue to use my computer for making music and write books- and do some design on it- Can I reinstal my UBUNTU- Delite all and start from buigining?- store my files somehow- if that is possibility- I&#8217;m open to it- just need help.
Thanx in advance.

---

### Post by CharlesA on 2011-11-08
> **sonja4flash said:**
> Was thinking noone wont get me seriously - only thing what I can do now is- what - turn on windows again- that I could continue to use my computer for making music and write books- and do some design on it- Can I reinstal my UBUNTU- Delite all and start from buigining?- store my files somehow- if that is possibility- I&#8217;m open to it- just need help.
Thanx in advance.

Use whatever works for you.

I'm still not even sure what you are trying to do. If you need to reset your user's password you can do it from the link that haqking provided.

You can do that from the recovery console, which you can access from Grub.

Friendly mod note: Please edit your previous post if you have more information instead of quad posting. Thanks.

---

### Post by 3rdalbum on 2011-11-08
Maybe you could say what your native language is, and see if someone else here can help you in your native language. There might be a forum for Ubuntu support in your language, or there might be a Linux User Group in your area who could help you.

---

### Post by sonja4flash on 2011-11-08
Dont understund why is so hard to accept I CONT DO IT FROM RECOVERY CONSOLE- like that link shoved. Is not working. And this quad /what evere quad means- is just to try to explane haw that looks on my ch is not swiss language. 
My native lenguige is - will understand Serbian, Croatian Bosnian-ch here  - is not Swiss is &#269; or &#263; -  was searching those data’s on their comuneteys here  but they are not serius at all- they mes with you- and then they lafe to you for egsampel tipe lVOR -they dont ekplane that what they did is - tipe  l   small L  in stead big I (i)

---

### Post by Elfy on 2011-11-08
Hi - it is very hard to understand what you are saying, though it seems that you are having some trouble changing a password - if you are not the admin of the machine then you might have issues.

There are support options available in languages other than English - there is in fact some Croatian support - perhaps you'd be better there not trying to use English 

[http://www.ubuntu.com/support/community/locallanguage#croation](http://www.ubuntu.com/support/community/locallanguage#croation)

---

### Post by sonja4flash on 2011-11-08
That is what community of yours is doing on Croatian- and I see here is hard to accept- i cont change pass on stereotype way. 
> all- they mes with you- and then they lafe to you for example type lVOR  -they don’t explane that what they did is - type  l   small L  in stead  big I (i)

Now you will say to me you don’t understand my English- or?

---

### Post by Elfy on 2011-11-08
If you can;t change the password in the normal way - then what happens when you do try to change it?

Are you trying to change just the password or are you trying to do more than that?

---

### Post by sonja4flash on 2011-11-08
I do everything like - for example that link where cat is in front of monitor say- and on final step is-  
> **sonja4flash said:**
> When I wrote pass for first time- i think- that’s it
When I retype pass- im in fier- but it doesn’t match to first one
i try third or second time, and fort time- all those times pass don’t match- then I’m upset cause I cont do nothing any more except  
step i did mention above- Shot down by violence. 
(can I call that reboot?)

This what happen- which part of English is not clear will take dictionary- and try to explane you.

---

### Post by sonja4flash on 2011-11-08
> **forestpiskie said:**
> If you can;t change the password in the normal way - then what happens when you do try to change it?

Are you trying to change just the password or are you trying to do more than that?
What more I can do without admin pass- i don&#8217;t have no mobile access, someone take my name on my mail  and my mail address  with all contacts, I live on edge of existantion (assume that will be hard to understand on English) because i did stay without my identity. Im willing to go back from whey best beginning of UBUNTU-  I can continue my life an work.

---

### Post by sonja4flash on 2011-11-08
On maybe I should try rhetorical way:

Which part of "Resseting pass tips not working " you don’t understand?

Pleas don’t send me back to "ch is not Swiss"  community

---

### Post by CharlesA on 2011-11-08
If the install is so messed up that you aren't able to access it, just boot off a livecd and copy all the stuff from your home directory to external media and then reinstall Ubuntu.

It would help if you could get us screenshots of the error you are getting when you try to change your password.

---

### Post by drmrgd on 2011-11-08
I *think* I may see a problem here.  If I understand you, you're trying to set your password to "im in fier" (please correct me if I'm wrong).  I think the issue you're having is the spaces in the password.  Try changing your password as you've been doing, but choose something without spaces in it like "iminfier".  I'm really hoping that helps you!

---

### Post by sonja4flash on 2011-11-08
Thanx again- but can just make photo of my computer in that unpleasant moment.  (what I will do in a while)
Tank you for tips with space in pass- maybe will start to use it.  Was newer so simple-minded and free in choosing my protection keys.

BTW haw can I reinstall Ubuntu without administration pass- could help- would like to use Ubuntu on English for example- at least that GRUB is on English- just take my CD device is not working as condition in which should reinstall Ubuntu and put my new admin key .

---

### Post by CharlesA on 2011-11-08
> **sonja4flash said:**
> Thanx again- but can just make photo of my computer in that unpleasant moment.  (what I will do in a while)
Tank you for tips with space in pass- maybe will start to use it.  Was newer so simple-minded and free in choosing my protection keys.

BTW haw can I reinstall Ubuntu without administration pass- could help- would like to use Ubuntu on English for example- at least that GRUB is on English- just take my CD device is not working as condition in which should reinstall Ubuntu and put my new admin key .
What are you talking about when you say "administration pass" ?

In a default install of Ubuntu, the user created during install has admin (sudo) access.

---

### Post by sonja4flash on 2011-11-08
story like 
format post!

---

### Post by Elfy on 2011-11-08
> BTW haw can I reinstall Ubuntu without administration pass-You can't do so - but you will know your new password - you'll not need to have a 'root' password as it is by default disabled.

If you want help with reinstalling then I would suggest that you backup data and then start a new thread. 

Please bear in mind though that it is better not to write 'story-like' posts - it doesn't help us to help you.



[Suggestions on how to get your support questions answered as quickly as possible ]("http://ubuntuforums.org/showpost.php?p=8920811&postcount=1")

---

### Post by sonja4flash on 2011-11-08
this was story like
Format post!

---

### Post by sonja4flash on 2011-11-08
> **forestpiskie said:**
> 

Please bear in mind though that it is better not to write 'story-like' posts - it doesn't help us to help you.



[Suggestions on how to get your support questions answered as quickly as possible ]("http://ubuntuforums.org/showpost.php?p=8920811&postcount=1")
  Thanks for tip- just for me is so komplex problematc- and by vocation- I’m not programmer.
Will try later new tird. stay in touch.

---

### Post by sonja4flash on 2011-11-08
keep in mined that quickest way is not always solution.
Ubuntu is not Ubuntu just because is Ubuntu.
don&#8217;t wont to preach here- but to understand problematic sometimes bigger picture is required.
If real help is offered- if is not ewer day job by default- 
didn&#8217;t log on no forums for ages shuld start
I&#8217;m new to Ubuntu- pleas help-

---

### Post by sonja4flash on 2011-11-08
[IMG]http://ubuntuone.com/7KQqXvNGuEdT4zZ2uaKY2o[/IMG]


Is this reason to be worried?
I also don&#8217;t understand my native language in programming- would help me as well that they use English.
If I wont to type n/y on this step- I cont.

---

### Post by CharlesA on 2011-11-08
You use ***sudo*** to run commands as admin (root) instead of switching to the root user.

See here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

So if you wanted to install that program, you would run this:

```
sudo apt-get install vim
```

---

### Post by sonja4flash on 2011-11-08
That shows  what need to be done to do this 
>  many new users try to take short cuts by enabling the root account,
yea- it seems stereotype I don’t need it for now.

---

### Post by CharlesA on 2011-11-08
> **sonja4flash said:**
> That shows  what need to be done to do this 

yea- it seems stereotype I don’t need it for now.

The thing is that you use sudo instead of enabling the root account.

Are you using sudo ?

---

### Post by Elfy on 2011-11-08
Given the problems you appear to be getting accomplishing things that should work and the other things you have alluded to I would think seriously about backing up your data and reinstalling.

I have no idea why you are trying to install root-system-bin - this thread is apparently about changing a password.

Where are you getting this other information from to send up these other paths you appear to be going.

I gave you one link to a non-English suppost system - there are others - perhaps one of them might suit you ?

[http://www.ubuntu.com/support/community/locallanguage](http://www.ubuntu.com/support/community/locallanguage)

IF you decide to reinstall then start a new thread - you can PM me the link of that thread if you do so and I will look in it then - but I'll not do PM support.

---

### Post by sonja4flash on 2011-11-08
> **CharlesA said:**
> The thing is that you use sudo instead of enabling the root account.

Are you using sudo ?
Yes. Was trying to  after all trys by changing pass i did try in GRUB did failed - to see what happens in sudo- maybe there i need to change user- you see
in link you gave me- on step- when should list all users on my account it doesn’t do so, was thinking because I’m only user. Haw should i switch to root user instead of admin(root), and why should I do so?

---

### Post by Elfy on 2011-11-08
You shouldn't switch to root user, you should use your ordinary user and then use sudo or gksudo (kdesudo in Kubuntu) to do root tasks.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by CharlesA on 2011-11-08
> **sonja4flash said:**
> Yes. Was trying to  after all trys by changing pass i did try in GRUB did failed - to see what happens in sudo- maybe there i need to change user- you see
in link you gave me- on step- when should list all users on my account it doesn’t do so, was thinking because I’m only user. Haw should i switch to root user instead of admin(root), and why should I do so?
Why do you keep talking about GRUB? That has nothing to do with changing your password unless you are trying to change it from recovery mode.

---

### Post by sonja4flash on 2011-11-08
are you aboard familiar with this error and why it is shown to me?

[IMG]http://ubuntuone.com/4wszaAujomSP2S48JgIZPm[/IMG]

This should be my  user admin account which pass did forgot-here it says

Is impossible to run Masface
Failure in  run process child "user-
admin" (there is not such a file or directory)

Close.

[IMG]http://ubuntuone.com/2zznL2etA1e92Wp2Cjck2O[/IMG]

---

### Post by sonja4flash on 2011-11-08
> **CharlesA said:**
> Why do you keep talking about GRUB? That has nothing to do with changing your password unless you are trying to change it from recovery mode.

Because I was learning- and didn’t wont to learn by mistake in recovery mode- was trying to see what will happened somewhere where it can harm so hard

---

### Post by audiomick on 2011-11-08
From the first post in the thread

> **sonja4flash said:**
> Did try everything, all /to me/ available  tips to change  but in 6 month with Ubuntu with [COLOR=Red]no Administration possibility[/COLOR] feel like someone else control my life, and I hate it. 
Can anyone help?
I can't help feeling that this whole thread started from a wrong idea. As you would have learned from the link about RootSudo that Forestpiksie posted, it is not true that you have no Administration possibilities in Ubuntu. Also, your system is quite well protected by the sudo setup as long as no-one knows your user password. For normal use, you do not need to worry about root at all.

---

### Post by sonja4flash on 2011-11-08
Son Charlesa-can you understand my "ch is not Swiss"  native problems. other way around we have simbol for dj not DJ it looks like &#273; or &#272; or Dž or dž- wouldn’t make big problem from it than in 2009 Linux community magazine didn’t come on adders where  was living in Croatia- but was on švabo- actualy German. - and Debian was instald in our offices, and someone from Switzerland stole my keyboard with my native letters.
Sorry for story like post .

---

### Post by sonja4flash on 2011-11-08
> **audiomick said:**
> From the first post in the thread


I can't help feeling that this whole thread started from a wrong idea. As you would have learned from the link about RootSudo that Forestpiksie posted, it is not true that you have no Administration possibilities in Ubuntu. Also, your system is quite well protected by the sudo setup as long as no-one knows your user password. For normal use, you do not need to worry about root at all.

Parachuter. As well if i don’t know it?

---

### Post by sonja4flash on 2011-11-08
I’m hitting that wall on and on- is it possible- before i did register my Ubuntu One did already had apps that looks like this  - on it?

[IMG]http://ubuntuone.com/6O6WZDuakSYXF9wjoVSc53[/IMG]

---

### Post by Jonathan L on 2011-11-08
Draga Sonja

Molim

Open Applications > Accessories > Terminal

Then run these two commands and post a screenshot of the result,

```
id
sudo id
```Hvala

Jonathan.

---

### Post by Elfy on 2011-11-08
> **Jonathan L said:**
> Draga Sonja

Molim

Open Applications > Accessories > Terminal

Then run these two commands and post a screenshot of the result,

```
id
sudo id
```Hvala

Jonathan.
Thank you Jonathan L

---

### Post by sonja4flash on 2011-11-08
Here it is- &#272;onatn.

[IMG]http://ubuntuone.com/30HlUAvLq9UUbKrqKn7cmU[/IMG]

---

### Post by Jonathan L on 2011-11-08
> **sonja4flash said:**
> Here it is- &#272;onatn.

[IMG]http://ubuntuone.com/30HlUAvLq9UUbKrqKn7cmU[/IMG]

Hvala!

Answer the question yes or no: do you know the password for the user 'korisnik'?

&#272;onatan

---

### Post by Elfy on 2011-11-08
Actually run the second command - enter then put in your password

```
hobgoblin@hobgoblin:~$ id
uid=1000(hobgoblin) gid=1000(hobgoblin) groups=1000(hobgoblin),4(adm),20(dialout),24(cdrom),46(plugdev),117(lpadmin),119(admin),124(sambashare)
hobgoblin@hobgoblin:~$ sudo id  
[sudo] password for hobgoblin: 
uid=0(root) gid=0(root) groups=0(root)
hobgoblin@hobgoblin:~$ 
```

Mine looks like this.

---

### Post by sonja4flash on 2011-11-08
Can do it that looks like this 
[IMG]http://ubuntuone.com/4lX9ccu7XAEDa3TAq9JQmC[/IMG]

But that is far I can get- because- i don’t know pass and I cont change it as I did mention in first few posts.

---

### Post by Jonathan L on 2011-11-08
> **sonja4flash said:**
> Can do it that looks like this 
[IMG]http://ubuntuone.com/4lX9ccu7XAEDa3TAq9JQmC[/IMG]

But that is far I can get- because- i don’t know pass and I cont change it as I did mention in first few posts.

Sonja --

Thank you.  Now we are absolutely clear.

Do you know how to boot into recovery mode?

Jonathan.

---

### Post by sonja4flash on 2011-11-08
Yes. Should I try to do so, Jonathan?

---

### Post by Jonathan L on 2011-11-08
Sonja --

> **sonja4flash said:**
> Yes. Should I try to do so, Jonathan?
No, not yet.

Please do this and show the result
```
ls -l /etc/passwd /etc/shadow /etc/group /etc/gshadow 
```Hvala

Jonathan.

---

### Post by sonja4flash on 2011-11-08
You are welcome, sorry for waiting.
[IMG]http://ubuntuone.com/3d5ta5V4C2dXXw1eBM5PzL[/IMG]

In mean time did made photos of boot recovery mode- if you need it.

Thanks for trying to help Jonathan.

---

### Post by Jonathan L on 2011-11-08
> **sonja4flash said:**
> You are welcome, sorry for waiting.
[IMG]http://ubuntuone.com/3d5ta5V4C2dXXw1eBM5PzL[/IMG]

In mean time did made photos of boot recovery mode- if you need it.

Thanks for trying to help Jonathan.

Hi Sonja

Please try that again.  You need the spaces like my example.

Hvala
Jonathan.

---

### Post by sonja4flash on 2011-11-08
I can but was precise- in first line are spaces like you did wrote
in second line is without spaces- did fall on my mind to do it just in case.

---

### Post by Jonathan L on 2011-11-08
> I can but was precise- in first line are spaces like you did wrote
...Hi Sonja

Perhaps it was not clear[FONT=monospace]
[/FONT]```
ls   -l   /etc/passwd   /etc/shadow   /etc/group   /etc/gshadow
```When you typed it there are some spaces missing.  Please try again.

Hvala
Jonathan.

---

### Post by sonja4flash on 2011-11-08
My apologise

[IMG]http://ubuntuone.com/0iuSTWqhcm5p2pMmgtQumD[/IMG]

---

### Post by Jonathan L on 2011-11-08
> **sonja4flash said:**
> My apologise

[IMG]http://ubuntuone.com/0iuSTWqhcm5p2pMmgtQumD[/IMG]

Hi Sonja

One more time please: you missed a / this time.  It is essential to be accurate: perhaps you can use cut-and-paste with the mouse (SHIFT-CTRL-V to paste into terminal window).

```
ls   -l   /etc/passwd   /etc/shadow [COLOR=Red]  /[/COLOR]etc/group   /etc/gshadow
```Hvala
Jonathan.

---

### Post by sonja4flash on 2011-11-08
[IMG]http://ubuntuone.com/1pRXun6AAH3aB2VYUyJGU8[/IMG]

Nema na cemu/ your welcome

Edit: could be easier that I can copy past- but I&#8217;m disabled to do so
Had to be honest- here  looks written as  I did before

---

### Post by Jonathan L on 2011-11-08
Sonja

Good.  Now do
```
date
```

We see that /etc/shadow was edited.  But surely it was more recently than 2011-04?

Hvala.
Jonathan.

---

### Post by sonja4flash on 2011-11-08
I was cheeking some** Important** data&#8217;s as orientation on my comp- and did found that did start to wrote them in OpenOffice droving- what is impossible   - cont get exact orientation when did lost all my data&#8217;s - except  if i get more time- that I can get out wit exact date of Interruption - or when pass is changed and that I didn&#8217;t done it .

Should I do so?

Hvala.

---

### Post by Jonathan L on 2011-11-08
> I was cheeking some** Important** data’s...

Sonja

I'm sorry I don't understand what you are saying.

Please just find the current date on your computer by typing this into a terminal window:
```
date
```

Hvala.
Jonathan.

---

### Post by sonja4flash on 2011-11-08
[IMG]http://ubuntuone.com/7LzRjPEMGE4dDnZJccxY1C[/IMG]

---

### Post by Jonathan L on 2011-11-08
Sonja

Hvala.  Ok all that is good.

You need to do two steps.

[SIZE=4]**1.  Reboot into recovery mode.**[/SIZE]

If there is more than one "recovery mode" in your menu then choose the first one.
[IMG]http://www.psychocats.net/ubuntu/images/resetpasswordoneiricthumb01.png[/IMG]http://www.psychocats.net/ubuntu/images/resetpasswordoneiric01.png


[SIZE=4]**2.  Get root shell and do the passwd command **[/SIZE]

Give the password command.  

```
passwd korisnik
```Then give your new password two times.

It will look exactly like this:
[IMG]http://www.psychocats.net/ubuntu/images/resetpasswordlucidthumb02.png[/IMG]
[http://www.psychocats.net/ubuntu/images/resetpasswordlucid02.png](http://www.psychocats.net/ubuntu/images/resetpasswordlucid02.png)

When you boot after that you should be able to do
```
id
sudo id
```With your new password.

Tell us what happens.  If you have a problem then say what was different from these screens.

Jonathan.


(Thanks to [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) for the instructions and pictures)

---

### Post by sonja4flash on 2011-11-08
In steed of
 [IMG]http://www.psychocats.net/ubuntu/images/resetpasswordlucidthumb02.png[/IMG]

I did found 

[IMG]http://ubuntuone.com/7Ic3jclECmAGuw5l6O2RGC[/IMG]

Just to could type   

```
ls /home 
```

type in 
```
passwd korisnik
```

would be asked for passwd and first time did look like
```
:
```
second time  was 
```
Login incorrect
```

Now I don’t know what to do in case of root pass for main entrance

What I’m doing wrong?


Hvala.
Sonja

---

### Post by sonja4flash on 2011-11-08
This is what will lead me on same space, maybe should try to do it now. Tell me if is necessary to do it now. I’m bit tired. But thanks for understanding my problems.
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by sisco311 on 2011-11-08
sonja

If you don't remember your user password and forgot the root password as well, then you will have to boot into a root shell and reset or lock the root password and reset your user password.


Reboot the computer and hold down the Shift key. 

When the grub menu appears use the arrow keys to highlight the recovery mode option. 

Press e for edit and replace the **ro single** kernel parameters at the end of the *linux* line with **rw init=/bin/bash**

Press Ctrl+x to boot the computer and wait for all boot processes to finish. 

Remount the root partition with read/write privileges:
```

mount -o remount,rw /

```

In order to lock the root account password run:
```

passwd -dl root

```

In case your user has no admin rights follow this instructions:
[http://www.psychocats.net/ubuntu/fixsudo#repaircommands](http://www.psychocats.net/ubuntu/fixsudo#repaircommands)

In order to reset your user's password run the following command:
```
passwd **username**
```
where **username** is your login name.

Press Ctrl+Alt+Del to reboot computer.

---

### Post by Jonathan L on 2011-11-08
> **sonja4flash said:**
> In steed of
 [IMG]http://www.psychocats.net/ubuntu/images/resetpasswordlucidthumb02.png[/IMG]

I did found 

[IMG]http://ubuntuone.com/7Ic3jclECmAGuw5l6O2RGC[/IMG]

Just to could type   

```
ls /home 
```type in 
```
passwd korisnik
```would be asked for passwd and first time did look like
```
:
```second time  was 
```
Login incorrect
```Now I don’t know what to do in case of root pass for main entrance

What I’m doing wrong?


Hvala.
Sonja

Sonja

I don't think you're doing anything wrong: it's a case of understanding exactly what situation your computer is in.  Follow Sisco's instructions to fix get to a shell prompt.

Jonathan.

---

### Post by sonja4flash on 2011-11-09
> **sisco311 said:**
> sonja

If you don't remember your user password and forgot the root password as well, then you will have to boot into a root shell and reset or lock the root password and reset your user password.


Reboot the computer and hold down the Shift key. 

When the grub menu appears use the arrow keys to highlight the recovery mode option. 

Press e for edit and replace the **ro single** kernel parameters at the end of the *linux* line with **rw init=/bin/bash**

Press Ctrl+x to boot the computer and wait for all boot processes to finish. 

Remount the root partition with read/write privileges:
```

mount -o remount,rw /

```In order to lock the root account password run:
```

passwd -dl root

```In case your user has no admin rights follow this instructions:
[http://www.psychocats.net/ubuntu/fixsudo#repaircommands](http://www.psychocats.net/ubuntu/fixsudo#repaircommands)

In order to reset your user's password run the following command:
```
passwd **username**
```where **username** is your login name.

Press Ctrl+Alt+Del to reboot computer.

Sisco tank you

in ```

mount -o remount,rw /

```can you precise spaces- This is what happens to me
```
 root@(none):/# -o   remount,rw   /
``````
[       126.798202] EXT4-fs (sda1): re-mounted. opts:errors=remount-ro
```When was deliting (by folowing instructions on this link [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)) 
 ```
ro singel
```and replacing it with

 ```
rw init=/bin/bash
```I’m on step Jonathan- you won’t me to be
What means here
[IMG]http://www.psychocats.net/ubuntu/images/resetpasswordlucidthumb02.png[/IMG]

(thanx to unknown for leaving keyboard where I am at the moment- no chance that could do this by using keyboard of my own)

---

### Post by sonja4flash on 2011-11-09
I did so

**ro singel **on end of linux line did replace with
```
rw init=/bin/bash
```
This time didn&#8217;t take me 
[IMG]http://www.psychocats.net/ubuntu/images/resetpasswordlucid02.png[/IMG]

In stead 
I did type
 after
```
root@(none):/#
```
```
ls /home
```it answer with 
**username**

I did type
passwd **username**

did ask me to 
```
Enter new UNIX passwd
```I did twice
did sad
```
 pass updated successfully
```so what I did after rebooting
did went to Terminal to type

```
id
sudo id
```and this is what I see
[IMG]http://ubuntuone.com/1mET5EFQejX9JYAPCMsBgk[/IMG]

Now just need to cheek can I use my computer like I would like to. 

Tanks to all of you for understanding.

---

### Post by sonja4flash on 2011-11-09
I need help haw to mark this topic as SLOWED


Yupi Yeah

---

### Post by nothingspecial on 2011-11-09
> **sonja4flash said:**
> I need help haw to mark this topic as SLOWED


Yupi Yeah

Done :)

Next time you can mark a thread solved by clicking "Thread Tools" at the top of the page.

---

### Post by matt_symes on 2011-11-09
Hi

@sonja4flash.

Some of your posts were difficult to understand.

You could try this.

Write your post in your own language. Google translate. 

Translate it to English and post that.

[B][http://translate.google.com/](http://translate.google.com/)

[/B]@ Sonja4flash. 

Neki od va&#353;e postove su te&#353;ko za razumjeti. 

Mogli biste probati ovaj. 

Napi&#353;ite svoj post u svoj jezik. Google Translate. 

To Prevedi na engleski i post da.

Edit: I have no idea how that translated into Croatian (i think that's the language) :D

Kind regards

---

### Post by sonja4flash on 2011-11-09
Dear,

I would recommend you to dont use  google translator on language you did to translate  text 
> 
Hi

@sonja4flash.

Some of your posts were difficult to understand.

You could try this.

Write your post in your own language. Google translate. 

Translate it to English and post that.

I understand you better if you use English.

Sincerely
Sonja

---

### Post by Jonathan L on 2011-11-09
> [...] and this is what I see
[IMG]http://ubuntuone.com/1mET5EFQejX9JYAPCMsBgk[/IMG]

Now just need to cheek can I use my computer like I would like to. 

Tanks to all of you for understanding.Sonja

Dobro! Dobro!  Well done looks like you've got it fixed.

Kind regards
Jonathan.

---

### Post by sonja4flash on 2011-12-20
My main Pass is interrupted again! Just as information to Ubuntu community!

---

