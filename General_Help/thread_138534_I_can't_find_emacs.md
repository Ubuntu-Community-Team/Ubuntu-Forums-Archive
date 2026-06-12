---
title: "I can't find emacs?"
date: 2006-03-02
forum: General Help
---

### Post by provost on 2006-03-02
Hi all,

About a month or two ago, I got Ubuntu CDs shipped to me from their
free shipping site and I installed it on a P3 750 Machine I have.

The version is Ubuntu 5.10.  My machine is at home and I have no
internet connection there.

Last night I hooked the machine up and went to have a look.  It's a
friendly sytem to use.  Everything seems to work well with me having
to configure anything major after the install (which also required
minimal techie knowledge)

I couldn't find emacs.  Does anyone know if it's on the install CD
anywhere?  When I did a search in what looks to be the "package"
managers, all I could find was things labeled as "frontend"s for
emacs.

I'm off to do some googling to check on this and also to check on
where to get emacs for ubuntu (maybe there is some Ubuntu package
type file I can download, bring home and double click to install).

If anyone has had any similar experience in this matter or has any
tips for working on Ubuntu without a net connection like I am, I'd
appreciate you sharing your wisdom on the matter here.

---

### Post by provost on 2006-03-02
I only found one article so far which says I might find luck in trying an advanced mode of the package manager so I'll go look for that tonight after work, Hopefully I won't come up against the same errors as he did.

Article is here: [http://www.weiqigao.com/blog/2005/12/12/ubuntu_5_10_first_impression.html](http://www.weiqigao.com/blog/2005/12/12/ubuntu_5_10_first_impression.html)

---

### Post by twigboy on 2006-03-02
Have you tried typing emacs in the terminal?
You might need to download it from Synaptic, just search for emacs, I had to do that for kate.

---

### Post by akiro.yamamoto on 2006-03-02
Emacs is on the install cd.
Search in Synaptic for emacs and it will come up, just click on it, select
"Mark for Installation" and it will select the other packages it needs. Click OK then Apply and your done. (It will ask for your Install CD).

---

### Post by provost on 2006-03-02
I did do a search for emacs.  no luck there.

I also went through the entire list under the "All" section and I couldn't find it there either.

I think emacs must have just been left out.

I even tried "apt-cache search emacs" as per the advice of a friend with no luck again.  I even went into trying it with wildcards :rolleyes:  eg "apt-cache search *emacs*" but no luck still

Should I go directly into the cd and look somewhere specific?


Anyway, I downloaded the source for emacs and after eventually getting the configure file to finish without errors, I have moved on to try and "make" it.  Lord help me it's giving out about calls to exit(2).  It's times like this I really miss the TAGS in emacs :cool:

---

### Post by petef on 2006-03-02
It's certainly their if you have internet access not sure about the CD as I downloaded Ubuntu.

Cheers

Pete

---

### Post by provost on 2006-03-02
Is it possible to download something like a ubuntu emacs package?

Ideally where I could just bring it onto my desktop and double click it to have emacs installed on my machine?

---

### Post by carlosqueso on 2006-03-02
[http://packages.ubuntu.com/breezy/editors/emacs21](http://packages.ubuntu.com/breezy/editors/emacs21) will give you the deb file to install with dpkg-i  <name of deb> however, you will also need to make sure you have everything listed as dependencies (stuff with red circles next to them).   Also, it's called emacs21, so maybe the name of the package will help.  Finally, it that's too much to do, ubuntu comes with nano and vim.  Both may be able to help you.

---

### Post by provost on 2006-03-03
I'll give it a shot.  Why not?:-k :twisted:

---

### Post by provost on 2006-03-09
No luck with the deb files.  I couldn't understand what to do there.

I gave a try installing from source but I got make errors due to calls to exit(2) in the code so I gave up.

---

### Post by hajk on 2006-03-09
The way to install new packages in Ubuntu is by using the Synaptic package manager (look at the System --> Administration menu); Synaptic is a front-end for the "apt-get" and "dpkg" functions. The sources for Synaptic and apt-get are listed in the file /etc/apt/sources.list; in your case, it probably just has the CD-ROM listed as source. As another poster has already explained, you can also manually download .deb packages, like emacs21, from some archive and copy them to your computer. Then you can install such a package with the command in a terminal (Applications --> Accessories -- Terminal)

sudo dpkg -i <............>.deb

where you'll have to replace <..........> with the full package name. (Double-clicking on such a package would require setting up file associations first, something most Ubuntu users don't bother with.)

It has already been explained to you that this MAY not work when the package has dependencies, meaning that it needs other packages to be installed first. In the case of emacs there would be several, like emacsen-common. Synaptic and apt-get handle these dependencies for you, but need a working internet connection. Installing packages by hand with dpkg requires that you consult the source and search for dependencies yourself, then download and copy those as well, and then install with dpkg in the right order....

May be you should stick with nano or vi for now...

---

### Post by ekins86 on 2008-03-03
Hey guys,
Don't know if anyone is still having problems with this, but I typed the following into the terminal and emacs installed fine:
sudo apt-get install emacs22

Hope that helps

---

