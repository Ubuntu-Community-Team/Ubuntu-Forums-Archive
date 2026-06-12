---
title: "i updated to ubuntu 10.4......HELPPP!"
date: 2010-12-29
forum: General Help
---

### Post by amna543 on 2010-12-29
[LEFT]OK so i updated to ubuntu 10.4 and as soon as it finished i turned my laptop off, i came back to it after an hour or so i turned it on it welcomed me with a purple screen daying ubuntu...........but then the screen went black and nothinh happened??:confused::confused::confused: after this i turned it off! please help me!!!! how do i get my laptop 2 work??? i wud be most grateful if any advice was given....:confused:[/LEFT]
thanx
x

---

### Post by Quackers on 2010-12-29
If it is the only operating system on the computer hold down the shift key whilst booting. This should bring up the grub menu, on which the top item (Ubuntu) will be highlighted.
At this point press the "e" key and a new screen will appear.
Navigate to the end of the line which says "quiet splash" then press back-space button to erase those words. Then type "nomodeset" - without the quotes, and then press ctrl + X to reboot.
See if that allows it to boot to the desktop. If it does you will need to install video drivers by running System > Admin > Hardware drivers (or Additional Drivers)

---

### Post by coffeecat on 2010-12-29
@amna543, I agree with Quackers to try the nomodeset option. You say you upgraded to 10.04. What version of Ubuntu were you using before and was it working OK? Also, do you know what type of graphics you have - nvidia, ati, intel or something else? If Intel do you know which chipset? There is a problem with older Intel and 10.04 and 10.10, but easily fixed.

---

### Post by amna543 on 2010-12-29
hi thanx alot for your reply
i followed your intructions and after i pressed ctrl and x the screen started to have aload of words on it and the screen went black again?? what now? 
thanx again

---

### Post by coffeecat on 2010-12-29
> **amna543 said:**
> what now? 

Answer my questions. :wink:

---

### Post by amna543 on 2010-12-29
im sorry but i dont know any of the ansers- im not very good wi computers and im a bit of a noob wi ubuntu....but do u know wat i can do 2 solve it? thanx

---

### Post by Quackers on 2010-12-29
Coffeecat asked the questions because the answer to your problem is dependent on the answers to his questions :-)
It appears that you may have a graphics card problem and it is not working fully so Ubuntu will not boot to the desktop. We can temporarily fix that if we can find the correct boot prompt (instead of nomodeset) to allow the desktop to load. Then you will be able to install the necessary drivers - maybe :-)
What is your exact model of laptop please?

---

### Post by amna543 on 2010-12-29
im not exactly sure but on the GRUB menu is the top version the model of the computer? thanx

---

### Post by coffeecat on 2010-12-29
> **amna543 said:**
> im not exactly sure but on the GRUB menu is the top version the model of the computer? thanx

No. The model of laptop is what the manufacturer calls it - something like "Sony Vaio" or "Acer Aspire" or "Dell Inspiron", but with a number as well. Have a look on the case. We need the manufacturer, model name, and, most importantly, number. Then Quackers, Google and I can find what your graphics card is and advise you. :)

---

### Post by Quackers on 2010-12-29
My laptop has a black Sony sticker on the bottom with the model number. Has yours anything similar?

---

### Post by amna543 on 2010-12-29
ohhhhhhh rit! ive got a dell inspiron 510m! thanx

---

### Post by Quackers on 2010-12-29
Google seems to suggest Intel's integrated Extreme graphics controller or Intel's integrated Extreme 2 graphics controller.
Coffeecat knows more about Intel graphics than me - I can guarantee that :-)

---

### Post by coffeecat on 2010-12-29
Aha! [http://www.laptops-battery.co.uk/blog/dell-inspiron-510m-review/](http://www.laptops-battery.co.uk/blog/dell-inspiron-510m-review/) Intel i855GM. I had a feeling in my water it might be. Or perhaps it was those pickled onions I had for lunch. Whatever...

Rather daunting link for you:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

But this is the bit you want:

> 
1) Hold down Shift while booting to enter the GRUB menu. 
2) Press 'e' to edit. 
3) Add "i915.modeset=1" after "quiet splash". 
4) Ctrl+x to boot.Let us know if this works and then either Quackers or I can tell you how to make it permanent.

---

### Post by amna543 on 2010-12-29
its worked! :D im on the home screen! how do i make it permanent??
thanx ALOT both coffeecat and Quackers!!!

---

### Post by coffeecat on 2010-12-29
> **amna543 said:**
> how do i make it permanent??

That link suggests you should turn KMS back on, but I would think this below would be better. What do you think, Quackers? Open a terminal, and...

```
gksudo gedit /etc/default/grub
```Find the line about 9 down that says:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```Edit  this to:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"
```Double-check that you have not made any typos, save the file and exit the text editor. Now:

```
sudo update-grub
```Close the terminal and see if you can reboot into a GUI. Let us know how you get on

---

### Post by Quackers on 2010-12-29
Looks mighty fine to me :-) Here's hoping!

---

### Post by amna543 on 2010-12-29
how do i reboot into a GUI? is it a command?

---

### Post by Quackers on 2010-12-29
Is there a switch symbol in the top bar at the far right? Click on that and one option should be restart.

---

### Post by amna543 on 2010-12-29
ohhh rit i thought u meant somet else.......its worked! :D so is it permanent now??

---

### Post by Quackers on 2010-12-29
It seems so :-)
Enjoy :-)
Nice one coffeecat!

---

### Post by coffeecat on 2010-12-29
> **amna543 said:**
> so is it permanent now??

If you edited /etc/default/grub the way I described and rebooted successfully without having to do anything else, then yes. :)

---

### Post by amna543 on 2010-12-29
oh thanks coffeecat and quackers!!! thanks again id litrelly be lost wiout u guys!!
thanks again! :DDDDDDDDDDDDDD

---

### Post by coffeecat on 2010-12-29
Good luck! Enjoy the Lucid Lynx. :)

---

### Post by Quackers on 2010-12-29
We like happy endings :-) You're welcome!
Can you mark the thread solved please, using the Thread Tools near the top of the page. Thanks.

---

