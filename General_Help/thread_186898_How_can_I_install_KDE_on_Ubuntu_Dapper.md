---
title: "How can I install KDE on Ubuntu Dapper?"
date: 2006-06-02
forum: General Help
---

### Post by kenweill on 2006-06-02
How can I install KDE on Ubuntu Dapper?

I have tried installing KDE on Breezy before but dont know how on Dapper.
What repositories should I add to have KDE?

Note: KDE only. Not the entire kubuntu-desktop.

---

### Post by bluevoodoo1 on 2006-06-02
You could try kde-core. Just gives the essential packages to use kde. 

"This metapackage includes the core official modules released with KDE. This
includes just the basic desktop (browser, file manager, text editor, control
center, panel, etc.) and important libraries and data, in addition to the
aRts soundserver."

Shouldn't have to add any additional repos.

---

### Post by murph2481 on 2006-06-02
Then when you boot up just click on session and change it to KDE or GNOME.  I also installed XFCE to see what that is like.  Its nice to have 3 different desktops to choose from.

---

### Post by pRedat0r on 2006-06-02
im not at my machine right now, but I believe you can do sudo apt-get install kubuntu-desktop to get access to KDE (session at login), or to install XFCE you would sudo apt-get install xubuntu-desktop

someone might want to verify that, but I thought I remembered seeing that several times in the dev forums.

---

### Post by kenweill on 2006-06-02
Okey.
Thanks alot. I just did install KDE from the repositories of Ubuntu Dapper. It downloads about 200Mb+.

I noticed. Istalling kubuntu-desktop only downloads about 100Mb+ while installing KDE downloads about 200Mb+. Whats the difference?

---

### Post by aysiu on 2006-06-02
If you want something light, take bluevoodoo1's suggestion: *kde-core*, which will install only the bare essentials of KDE.

The *kde* package installs everything (a lot, in other words), and the *kubuntu-desktop* package installs Ubuntu's custom KDE desktop, which is less than *kde* but a lot more than *kde-core*.

---

### Post by fornix on 2006-06-03
One really dumb question. Will i find all the programs already installed in ubuntu when i install kubuntu desktop. For example ubuntu has gaim, will kubuntu automatically place a link for gaim in its appropriate location when i log in kde?

---

### Post by Rackerz on 2006-06-03
[QUOTE=fornix]One really dumb question. Will i find all the programs already installed in ubuntu when i install kubuntu desktop. For example ubuntu has gaim, will kubuntu automatically place a link for gaim in its appropriate location when i log in kde?[/QUOTE]

It will indeed.

---

### Post by M4LFUNCT10N on 2006-06-03
Okay, so I just tried "sudo apt-get kubuntu-desktop" from the terminal, and I get "E: Invalid operation kubuntu-desktop"  What am I missing here?  Do I need to edit my sources.list?  I've got all the repositories enabled from synaptic.

---

### Post by Tartin on 2006-06-03
[QUOTE=M4LFUNCT10N]Okay, so I just tried "sudo apt-get kubuntu-desktop" from the terminal, and I get "E: Invalid operation kubuntu-desktop"  What am I missing here?  Do I need to edit my sources.list?  I've got all the repositories enabled from synaptic.[/QUOTE]

You forgot the install command...

sudo apt-get **install** kubuntu-desktop

---

### Post by M4LFUNCT10N on 2006-06-03
[QUOTE=Tartin]You forgot the install command...

sudo apt-get **install** kubuntu-desktop[/QUOTE]

Doh!  lol

](*,)     :o

---

### Post by M4LFUNCT10N on 2006-06-03
Okay, so I've got KDE and XFCE running, and I used the *-desktop method.  I've got one problem though, I've got tons of new programs.  I would *like* to hide KDE specific programs when in the other two desktop managers, and the same when I'm in GDE and XFCE.  Is there a way to do this?

---

### Post by shane2peru on 2006-06-03
Hey, this is a good thread, as I too am interested in looking at these desktops.  I'm installing kubutnu-desktop, and then I will try the XFCE or whatever it was.  Is there a way to limit the programs to the specific desktop?  Thanks, great topic!

Shane

---

### Post by stalefries on 2006-06-03
Right click the applications menu (assuming you're in Gnome) and click edit menu. You can figure it out from there.

---

