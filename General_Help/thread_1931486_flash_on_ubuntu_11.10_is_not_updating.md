---
title: "flash on ubuntu 11.10 is not updating"
date: 2012-02-25
forum: General Help
---

### Post by hunterkasy on 2012-02-25
I have a machine that is running ubuntu 11.10 64 I have ubuntu restricted install, flash has been working fine for several months but now the last couple of weeks it seems like flash is not getting updated. for examble on FB, some games will play but wine about flash being outdated and on other games it will not play because of flash being outdated.

I have a couple other copmuters running the same version and software and I am not having any problems with them

any help on getting flash happy again?

---

### Post by josephmills on 2012-02-25
Have you tried to install medibuntu [http://medibuntu.org/repository.php](http://medibuntu.org/repository.php) ?
hope that this helps

---

### Post by hunterkasy on 2012-02-25
> **josephmills said:**
> Have you tried to install medibuntu [http://medibuntu.org/repository.php](http://medibuntu.org/repository.php) ?
hope that this helps

I installed ubuntu 11.10 direct never did any upgrade

---

### Post by josephmills on 2012-02-25
> **hunterkasy said:**
> I installed ubuntu 11.10 direct never did any upgrade

while I would try and install medibuntu then after that If still not working I would install flash from source 
[http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)

down load the tar file open terminal (ctrl+alt+t)
```
cd ~/Downloads 
```
then 
```
tar -xvf install_flash_player* 
```
that is it you know should have flash.(well flash 11)
hope hat this helps

---

### Post by hunterkasy on 2012-02-25
Shockwave Flash 10.1 r999.

this is still the version I have on the computer

---

### Post by josephmills on 2012-02-25
> **hunterkasy said:**
> Shockwave Flash 10.1 r999.

this is still the version I have on the computer

remove the old one and re-install the n new one sorry I should have said that above

---

### Post by hunterkasy on 2012-02-25
> **josephmills said:**
> remove the old one and re-install the n new one sorry I should have said that above

I went into software center search for flash selected the one that is installed removed it, did what you trold me to from one of the above post, it still says the old flash version.

---

### Post by hunterkasy on 2012-02-25
can someone tell me what I am doing wrong, I am asure I am doing something wrong

---

### Post by josephmills on 2012-02-25
> **hunterkasy said:**
> can someone tell me what I am doing wrong, I am asure I am doing something wrong


**EDIT**

ok after reading above again you are on a 64 bit. Lets try this 
```
sudo apt-get --purge remove flashplugin-*

```
then
```
sudo add-apt-repository ppa:sevenmachines/flash 

```
then 
```
sudo apt-get update
```
then
```
sudo apt-get install flashplugin64-installer

```
then 
```
sudo add-apt-repository -r ppa:sevenmachines/flash 
```
then reboot what type of flash is installed ?

---

### Post by winh8r on 2012-02-25
Hi , sorry to barge in here, but it may be worth giving Flash Aid a try to resolve any conflicts and get everything back to normal .

Just click on the "Help with Flash" link in my sig below and follow the instructions there.

Hope this works and gets it resolved for you.

---

### Post by hunterkasy on 2012-02-25
> **josephmills said:**
> WAIT on this 
```
sudo apt-get --purge remove flashplugin-*

```
then 
[b]wait are you running 64 bit or 32 bit ? 
also what is your browser of choice ? [/b]thanks

I am running 64bt ubuntu I use FF

---

### Post by josephmills on 2012-02-25
> **hunterkasy said:**
> I am running 64bt ubuntu I use FF
Cool please see the post that I edited like 2 back if you are a firefox user there is also this [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) 
but do not know if that will help or hinder things. Just want to be honest. I have never installed that myself.
**edit**
but seeing from a different user that it looks like it is a great thing
sorry winh8r must have been editing a post or something when you posted that. thanks

---

### Post by hunterkasy on 2012-02-25
> **winh8r said:**
> Hi , sorry to barge in here, but it may be worth giving Flash Aid a try to resolve any conflicts and get everything back to normal .

Just click on the "Help with Flash" link in my sig below and follow the instructions there.

Hope this works and gets it resolved for you.

your flash aid fixed the problem

thanks everyone for your help I do really appreciate it alot

---

### Post by winh8r on 2012-02-26
Glad you got the issue solved.

The real credit should go to forum member [[COLOR="Red"]lovinglinux[/COLOR]]("http://ubuntuforums.org/member.php?u=649167")[COLOR="Black"] who created Flash Aid and has taken much of the pain out of getting Flash configured and running in most cases.

I just jumped in with the suggestion as it would save josephmills a good deal of figuring out what was going wrong, and it seemed to work.

Good Luck[/COLOR]

---

