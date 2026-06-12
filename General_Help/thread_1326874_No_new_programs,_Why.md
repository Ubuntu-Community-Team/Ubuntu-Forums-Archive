---
title: "No new programs, Why?"
date: 2009-11-14
forum: General Help
---

### Post by FelixS on 2009-11-14
I have installed the Ubuntu 9.10 64 bit version in my computer, but when I go to the applications menu, open the Ubuntu Software Center, select a program from there and try to install it doing click in the install button nothing happens. Why? :x

---

### Post by jorgecarrillo150990 on 2009-11-20
Im having the same problem with the normal 9.10 (not 64 bits).
Can anyone help us?

---

### Post by Slimbo on 2009-11-20
In Terminal:
```
sudo apt-get install scrot
```

What's the output ?

---

### Post by jorgecarrillo150990 on 2009-11-20
Sorry about the lack of trust here, but may I ask what scrot is?
A long time ago some guy thought it would be funny for me to put some command lines that crashed my system.

---

### Post by Slimbo on 2009-11-20
> **jorgecarrillo150990 said:**
> Sorry about the lack of trust here, but may I ask what scrot is?
A long time ago some guy thought it would be funny for me to put some command lines that crashed my system.

```
sudo aptitude show scrot
```

If you don't know what it means and are too scared from it, Google is waiting for you.

---

### Post by jorgecarrillo150990 on 2009-11-20
Again, I am sorry if I am offending you, but I did my Google search and it said it was a screenshot taker.

How is a screenshot taker help us solving our problems with Ubuntu Software Center?

---

### Post by Slimbo on 2009-11-20
> **jorgecarrillo150990 said:**
> 
How is a screenshot taker help us solving our problems with Ubuntu Software Center?

How can I know what's wrong without seeing the output ? How can you get the output without installing anything ? You can't! That's why I gave you guys a command which would try to install scrot and you could show us the output so we could start fixing your issues.

[COLOR=Gray][-- confused --][/COLOR]

---

### Post by FelixS on 2009-11-20
I think that this have a relation with the authorizations, because when it have to request me a password, but it don't do that. I said authorizations because there are many things that I can't do by that.

Am I right?:roll::-k

---

### Post by 3rdalbum on 2009-11-20
One of the possible reasons why software can't be installed is because of some sort of error. Software Center won't tell you error messages yet, so that's why we need you to try and install some software on the command-line. Once you do that, we'll be able to see if there's an error message, or if the software correctly installs.

Scrot is safe to install. Or you can choose a different package. Just as long as it's something you don't already have, that's fine.

---

### Post by lisati on 2009-11-20
> **FelixS said:**
> I think that this have a relation with the authorizations, because when it have to request me a password, but it don't do that. I said authorizations because there are many things that I can't do by that.

Am I right?:roll::-k

Do you mean that your password doesn't show on the screen when you type it in?

---

### Post by judge jankum on 2009-11-20
A screen shot is how I've gotten much help on this forum, and so far EVERYONE has been great to help....I trust these guys....I know as much about Linux as I do building a space ship lol" These guys saved my back side a few times....

---

### Post by jorgecarrillo150990 on 2009-11-21
Well, sorry for doubting and now here is the screenshot of the terminal while installing scrot
[http://i73.photobucket.com/albums/i222/MexAlbum/Screenshot-1.png]("http://i73.photobucket.com/albums/i222/MexAlbum/Screenshot-1.png")

Anyway, scrot is a Horrible name for an app, and that's why I was suspicious :P

Again, I am very sorry and I apologize :)

---

### Post by Prodigal Son on 2009-11-21
Does it produce any suspicious output when launched from the command line ?

```
gksudo software-center
```

---

### Post by jorgecarrillo150990 on 2009-11-21
> **Prodigal Son said:**
> Does it produce any suspicious output when launched from the command line ?

```
gksudo software-center
```

I did some experimenting and:
a) using the command line gksudo software-center asked me to introduce my password, I did and software center worked installing and removing.

b) I opened Software center again from the dropdown menu, the problem persisted since it didn't ask me password.

SMALL WORKAROUND

Left click on the menu bar and Choose "Edit Menus"
GO in applications

Go to "Ubuntu Software Center" and press edit.
In the line that says command  put
```
gksudo software-center 
```

Then click OK.

Now you can use the Ubuntu Software Center to install and remove apps.

---

### Post by judge jankum on 2009-11-21
scrot for a name is a little different. LOL!!!!!

---

