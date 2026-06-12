---
title: "How to Install fonts"
date: 2012-03-22
forum: General Help
---

### Post by GreatDanton on 2012-03-22
HI!
I was looking for gothic fonts (something like old English font), and i did not find anything on ubuntu software center. Can anybody help me with installing something that looks like old english font.

---

### Post by haqking on 2012-03-22
[https://answers.launchpad.net/ubuntu/+source/xorg/+question/183555](https://answers.launchpad.net/ubuntu/+source/xorg/+question/183555)

---

### Post by GreatDanton on 2012-03-22
This solution doesnt work for me. I cant open ttf file, I also cant paste it to the fonts. Also terminal wont install. Solution (iam new to linux so please provide easy solution).

---

### Post by idoitprone on 2012-03-22
> **GreatDanton said:**
> This solution doesnt work for me. I cant open ttf file, I also cant paste it to the fonts. Also terminal wont install. Solution (iam new to linux so please provide easy solution).

/usr/share/fonts/truetype/

perhaps open nautilus with root permissions and copy the ttf file to the directory above

```
gksu nautilius
```

---

### Post by haqking on 2012-03-22
> **GreatDanton said:**
> This solution doesnt work for me. I cant open ttf file, I also cant paste it to the fonts. Also terminal wont install. Solution (iam new to linux so please provide easy solution).

you cant open it, paste it or install it ?

Then you are having more problems than just font related ;-)

[http://askubuntu.com/questions/55688/is-there-a-graphical-way-of-installing-fonts-in-11-10-gnome-3](http://askubuntu.com/questions/55688/is-there-a-graphical-way-of-installing-fonts-in-11-10-gnome-3)

and i wasnt providing a install solution, i provided a link to where you could get old english fonts, you didnt mention in OP that you had issues installing them

---

### Post by GreatDanton on 2012-03-22
thanks for reply, but i still cant install font. I have downloaded the file, but i cant copy paste it into usr/share/fonts/truetype.

I dont understand how to install it with terminal commands (what is this nautilius?). Could you provide more clear answer? (step by step)!

Thank you.

---

### Post by haqking on 2012-03-22
> **GreatDanton said:**
> thanks for reply, but i still cant install font. I have downloaded the file, but i cant copy paste it into usr/share/fonts/truetype.

I dont understand how to install it with terminal commands (what is this nautilius?). Could you provide more clear answer? (step by step)!

Thank you.

the link wasnt step by step enough ?

what error are you getting ?

have you tried sudo as already posted ?

we need your steps taken and error messages.

---

### Post by GreatDanton on 2012-03-22
OK here we go. I use this link.
[http://www.wikihow.com/Install-Custom-Fonts-in-Ubuntu-10.10](http://www.wikihow.com/Install-Custom-Fonts-in-Ubuntu-10.10)

Thats the second time i tryed (previous i tryed that thing with  gsknautilius-it asks me for password but the second time i oppened the terminal i dont need to type password)
1. Open terminal
2.type:sudo mkdir /usr/share/fonts/truetype/custom2 (i dont have to type password-why idont know)
3i type just like in the link:sudo nautilius     ------i get sudo:nautilius:command not found.

What now?

---

### Post by haqking on 2012-03-22
> **GreatDanton said:**
> OK here we go. I use this link.
[http://www.wikihow.com/Install-Custom-Fonts-in-Ubuntu-10.10](http://www.wikihow.com/Install-Custom-Fonts-in-Ubuntu-10.10)

Thats the second time i tryed (previous i tryed that thing with  gsknautilius-it asks me for password but the second time i oppened the terminal i dont need to type password)
1. Open terminal
2.type:sudo mkdir /usr/share/fonts/truetype/custom2 (i dont have to type password-why idont know)
3i type just like in the link:sudo nautilius     ------i get sudo:nautilius:command not found.

What now?

so what error message do you get using the font installer then as in the link i provided ?

---

### Post by GreatDanton on 2012-03-22
ok i screenshot the window
Edit:if i try to copy paste to font folder, nothing happens. The file just slide back form where i dragged it.

---

### Post by haqking on 2012-03-22
> **GreatDanton said:**
> ok i screenshot the window
Edit:if i try to copy paste to font folder, nothing happens. The file just slide back form where i dragged it.

ok first of all you are not answering my question.

second of all nautilus is spelled nautilus and not nautilius

also you should use gksudo for graphical apps

so as i asked before what happens when you use the font installer as outlined in the link i posted ?

Cheers

---

### Post by GreatDanton on 2012-03-22
Thx for your time.
Ok i now i type sudo nautilus in terminal and it give me:sudo:nautilus:command not found.

If i understand right, you mean what happened if i double click on .tff file.

It says something like unable to read, or i dont have a program for opening this kind of file. (iam not sure, because that happened to me 3 hours ago, and i have already changed the program for opening-i thought xarchiver will open that, but it wont :( and now i dont know what said the first message.)

Edit: if now doubleclick on the file it says :cant open file. Archive format not recognized!


What kind of font installer do you mean, because i dont have any.

---

### Post by idoitprone on 2012-03-23
> **GreatDanton said:**
> OK here we go. I use this link.
[http://www.wikihow.com/Install-Custom-Fonts-in-Ubuntu-10.10](http://www.wikihow.com/Install-Custom-Fonts-in-Ubuntu-10.10)

Thats the second time i tryed (previous i tryed that thing with  gsknautilius-it asks me for password but the second time i oppened the terminal i dont need to type password)
1. Open terminal
2.type:sudo mkdir /usr/share/fonts/truetype/custom2 (i dont have to type password-why idont know)
3i type just like in the link:sudo nautilius     ------i get sudo:nautilius:command not found.

What now?

sudo usually require a password since your using other user's account to do something. If you do not have a password, then just type enter

that link wanted you to make a custom folder so you can keep track of you custom fonts

copy this to the terminal window
the gksudo is meant so you can have proper permission to edit /usr/ dir which is owned by root

you dont have to type it in
just copy and paste with mouse
```
gksudo nautilus /usr/share/fonts/truetype/
```open another folder with the directory of the font
drag the file over to the folder that you open with the command above

run this in terminal when done
```
sudo fc-cache -f -v
```


> **Manually**

 There are various locations in GNU/Linux in which fonts can be kept. These locations are defined in /etc/fonts/fonts.conf; standard ones include /usr/share/fonts, /usr/local/share/fonts, and /home/<username>/.fonts (where <username> is your user name). 
The  easiest way to install a truetype font is to press alt-F2 and enter the  following code (this will open nautilus in the right directory): 

gksu nautilus /usr/share/fonts/truetypeThen  create a new directory, name the directory whatever you like (choose a  name that you remember if you ever need to backup your fonts personal  fonts). Copy the fonts into that directory and finally rebuild the font  information files by pressing alt-F2, mark 'run in terminal' so you can  see the progress and entering the following code: 

sudo fc-cache -f -v
[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

### Post by GreatDanton on 2012-03-24
thanks for reply.
That didnt solved my problem. If i copy and paste the code into the terminal:gksudo nautilus /usr/share/fonts/truetype/
This code doesnt open the folder, like it should. why this code doesnt want to open folder with fonts I dont know, and i still cant copy paste font into the folder.

any solutions?

---

### Post by idoitprone on 2012-03-24
> **GreatDanton said:**
> thanks for reply.
That didnt solved my problem. If i copy and paste the code into the terminal:gksudo nautilus /usr/share/fonts/truetype/
This code doesnt open the folder, like it should. why this code doesnt want to open folder with fonts I dont know, and i still cant copy paste font into the folder.

any solutions?


it should open a pop up box prompt you for your pasword?

---

### Post by Toz on 2012-03-24
If you're using xubuntu, you may not have nautilus installed (it isn't installed by default). Instead, try:
```
gksudo thunar /usr/share/fonts/truetype/
```

---

### Post by GreatDanton on 2012-03-25
Thank you very much toz, and all who tried to help me!
Thats the soultion.

gksudo thunar /usr/share/fonts/truetype/

sudo fc-cache -f -v



Now i have my font installed!
Thanks

---

