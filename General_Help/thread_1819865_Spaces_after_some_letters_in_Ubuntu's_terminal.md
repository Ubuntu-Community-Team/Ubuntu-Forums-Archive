---
title: "Spaces after some letters in Ubuntu's terminal"
date: 2011-08-06
forum: General Help
---

### Post by Morian_3 on 2011-08-06
Hi guys,

I have strange issue with ubuntu's terminal lately it's showing up a space after some letters such as " t l f j i " 
when I tried to write a command by any of these letters I have got it, this problem is preventing me to implement any correct command 

so is it pkg issue need to re-install or I have to do something ?

my OS is ubuntu 11.04 natty with gnome unity GUI/ UTF-8 |  all my fonts that are using on my machine is Arial.

[IMG]http://i.imgur.com/OOvWO.jpg[/IMG]

---

### Post by papibe on 2011-08-06
By any chance did you custom your ~/.bashrc ?

Could you post the result of this command?
```
$ echo "$PS1"
```
Regards.

---

### Post by Morian_3 on 2011-08-06
> **papibe said:**
> By any chance did you custom your ~/.bashrc ?

Could you post the result of this command?
```
$ echo "$PS1"
```Regards.

No I didn't, this is the output of your command 

```

\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$ 


```

---

### Post by papibe on 2011-08-06
Does 'Terminal -> Reset and Clear' solve it?

If you initiate a new instance of bash, Does it have the same behavior?
```
$ bash
```
Just some thoughts,
Regards.

---

### Post by bodhi.zazen on 2011-08-06
> **papibe said:**
> Does 'Terminal -> Reset and Clear' solve it?

If you initiate a new instance of bash, Does it have the same behavior?
```
$ bash
```
Just some thoughts,
Regards.

Or reset

```
reset
```

---

### Post by Morian_3 on 2011-08-06
> **papibe said:**
> Does 'Terminal -> Reset and Clear' solve it?

.

No.

> 
If you initiate a new instance of bash, Does it have the same behavior?
 	Code:
 	$ bash 
Just some thoughts,
Regards.



I dunno what you are exactly mean but I checked out .bashrc file on my home dir and it's not has any problem in his letters also I haven't any issue while types this command on terminal.

---

### Post by Morian_3 on 2011-08-06
> **bodhi.zazen said:**
> Or reset

```
reset
```

I've been tried it, no positive result. :(

---

### Post by papibe on 2011-08-06
> **Morian_3 said:**
> 
I dunno what you are exactly mean but I checked out .bashrc file on my home dir and it's not has any problem in his letters also I haven't any issue while types this command on terminal.
I'm trying to determine if the problem comes from bash or gnome-terminal. You see, if it were related to gnome-terminal, the new bash instance 'may be' free of the errors.

Regards.

---

### Post by bodhi.zazen on 2011-08-06
1. Start another terminal, both gnome-terminal and say xterm.

2. If the problem persists, move your ~/.bashrc

```
mv ~/.bashrc ~/bashrc
```

And again open a new terminal.

If #2 solves the problem it is something in .bashrc

---

### Post by Morian_3 on 2011-08-06
> **papibe said:**
> I'm trying to determine if the problem comes from bash or gnome-terminal. You see, if it were related to gnome-terminal, the new bash instance 'may be' free of the errors.

Regards.


I see dude.

---

### Post by Morian_3 on 2011-08-06
> **bodhi.zazen said:**
> 1. Start another terminal, both gnome-terminal and say xterm.

2. If the problem persists, move your ~/.bashrc

```
mv ~/.bashrc ~/bashrc
```And again open a new terminal.

If #2 solves the problem it is something in .bashrc

The problem has been gone with xterm, what's the next step now ?

---

### Post by bodhi.zazen on 2011-08-06
Open a (gnome) terminal and look at the options.

Edit-> Profile preferences

Anything unusual in the fonts ? I think "Use the system fixed width font" is default.

Does setting an alternate font make a difference (make note of the default =) )

---

### Post by Morian_3 on 2011-08-07
> **bodhi.zazen said:**
> Open a (gnome) terminal and look at the options.

Edit-> Profile preferences

Anything unusual in the fonts ? I think "Use the system fixed width font" is default.

Does setting an alternate font make a difference (make note of the default =) )

Unfortunately, that option in profile preference doesn't make any change for this issue I tried to disable it then enable it again, it just change the size of texts on terminal box but the problem is still remaining.


here are pics for what's happening when check and uncheck on that option :

```

With check :
http://i.imgur.com/7SBpL.jpg

``````

Without check :
http://i.imgur.com/tovJI.jpg



```Any thoughts ?

---

### Post by bodhi.zazen on 2011-08-07
Ive not seen this before. Sounds as if it is related to gnome terminal.

Perhaps file a bug report on Launchpad or perhaps someone with more experience with gnome-terminal will have a suggestion.

As a work-around will xterm do for now ? I also use sakura (it is another alternate terminal).

---

### Post by Morian_3 on 2011-08-07
> **bodhi.zazen said:**
> Ive not seen this before. Sounds as if it is related to gnome terminal.

Perhaps file a bug report on Launchpad or perhaps someone with more experience with gnome-terminal will have a suggestion.

As a work-around will xterm do for now ? I also use sakura (it is another alternate terminal).

Yeah, in this time i will stick around on xterm till finds someone has a solution for that gnome-terminal.

Thanks a lot for your help. :)

---

