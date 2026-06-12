---
title: "camara"
date: 2009-10-28
forum: General Help
---

### Post by rastro123 on 2009-10-28
Hi, does anyone know how to get a cam to work in kopete and willing to shared this valued info with me? Im absolutely sick of trying and sick of having to go back and boot in windows only to chat to my bird in yahoo's messenger. I don't understand why when I tell it to install kopete in the synaptic manager, the cam never works- why only get half of the program? I've been using ubuntu for a year now and only ever have cam working in amsn, never in kopete. I just tried again, and it only makes me mad. I found some instructions here and: 
 Re: Kopete + Jasper + Webcams...
The basic install of any program via source is this:

Fire up the terminal batman !

Applications > Accessories > Terminal

then download the file to your desktop and

Code:

 cd Desktop

in terminal

then

Code:

 cd <jasperFileNameHere>

then

Code:

./configure

then

Code:

make

then

Code:

sudo make install

Hopefully this works, but you may recieve errors regarding dependicies (Packages which are missing which are needed to make the program works)

If you have missing dependicies, try and search for them in synaptic package manager first, then search the forum and if not make a thread
__________________
My BLOG for new Ubuntu Linux users // Install ANYTHING in Ubuntu // Ubuntu Linux help


So I follow this guys instructions and all I get is ''the desk top is not a directory'':
boo@boo-laptop:~$ cd Escritorio
boo@boo-laptop:~/Escritorio$ cd jasper-1.900.1.zip
bash: cd: jasper-1.900.1.zip: No es un directorio
boo@boo-laptop:~/Escritorio$ cd jasper-1.900.1.zip
bash: cd: jasper-1.900.1.zip: No es un directorio
boo@boo-laptop:~/Escritorio$ 

I asked some guy a while ago about this and he more or less told me to forget using kopete for a cam, but surely someone must know what to do to make it work. I hate having to go to windows just to chat with a cam.
many many thanks if anyone will help me!

---

### Post by Giblet5 on 2009-10-28
I sure do! :)

And if you hadn't decided to spam this forum by posting the same request repeatedly, I would tell you how.

---

