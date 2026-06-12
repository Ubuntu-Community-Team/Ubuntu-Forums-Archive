---
title: "Will I like KDE and Kubuntu and can I retain /home/user"
date: 2011-06-28
forum: General Help
---

### Post by ianc1 on 2011-06-28
I am thinking of changing from Ubuntu (Unity) to Kubuntu.  I don't know why I just fancy a change.  I know Unity was a big change and to be honest I quite like it, but I hear a lot about Kubuntu in podcasts and fancy giving it a try.

I know programs that are for Gnome will also work under KDE and vice versa.  My question is if I don't want many of the default packages (ie I want Firefox not Konqueror, Thunderbird not Kontact, Banshee not Amarok, etc) is this a bad start and a sign I won't like KDE in general.

I hear its heavier on system requirements as well, what sort of difference are we looking at here?

Also can I retain my current ~ directory as is or will all the Gnome stuff in it cause issues?

On comments and pros/cons of the swap over would be much appreciated.

Cheers

---

### Post by SoFl W on 2011-06-28
I believe you can install KDE and XFCE and run it along side gnome.  You select which manager you want when you log in.

---

### Post by snowpine on 2011-06-28
+1; just install the "kubuntu-desktop" package and you can try KDE while keeping all your installed applications, settings, and /home documents.

---

### Post by ianc1 on 2011-06-28
Thanks.  If I don't like it will the following remove it completely along with any hidden directories etc it places in ~ or will they remain.

```
apt-get purge kubuntu-desktop
```If its the latter I suppose I could do a recursive directory list before  and after the install and a diff of the two outputs to work out what it  installed.

---

### Post by FormatSeize on 2011-06-28
> **ianc1 said:**
>  
I know programs that are for Gnome will also work under KDE and vice versa. My question is if I don't want many of the default packages (ie I want Firefox not Konqueror, Thunderbird not Kontact, Banshee not Amarok, etc) is this a bad start and a sign I won't like KDE in general.
It's not really a sign that you won't like it. If you liked Unity, you will probably like KDE. As for the programs, you can uninstall the ones you don't want and install the ones that you want pretty easily. I completely sympathize with your wanting to use programs that you have grown to like. For me, it's always Audacious or Rythmbox over Amarok (it's a crash-fest for me), but I always find myself not being able to live without Kate and kb3. 
 
> **ianc1 said:**
> I hear its heavier on system requirements as well, what sort of difference are we looking at here?
If you can handle Unity, you likely have the processing power to handle KDE. As for what kind of differences, if Unity is a bison, then KDE is an elephant that swallowed another elephant. The good thing is that KDE is so highly configurable (perhaps too configurable) that you can change it so that it's not so taxing on your system and might even look a lot like something lighter. 
 
> **ianc1 said:**
> Also can I retain my current ~ directory as is or will all the Gnome stuff in it cause issues?
Did you set your home directory on a seperate partition? If not, then you either need to back it up so that you have it when you migrate over to KDE (it should be backed up anyway). 
 
> **ianc1 said:**
> On comments and pros/cons of the swap over would be much appreciated.

KDE is great if you like a highly polished operating system. It looks great, and smells great. It has all the special effects and compositing is enabled by default, so it looks great out of the box. Like I said before, it's highly, highly configurable. You could spend hours making KDE into your perfect, unique desktop environment.
 
There are too many cons for me to list here about KDE, but it's not really because it's bad, but my own, vague and nebulous personal opinions about KDE. So they aren't rigid things that will be true, and you may believe the opposite. As a matter of fact, I'm surprised I actually (finally) said some good things about it. Beyond personal opinion, there are no factual cons about KDE that I can think of if you have the hardware. Well, besides the Amarok crashes, but that could just be my experience.

---

### Post by snowpine on 2011-06-28
> **ianc1 said:**
> Thanks.  If I don't like it will the following remove it completely along with any hidden directories etc it places in ~ or will they remain.

```
apt-get purge kubuntu-desktop
```If its the latter I suppose I could do a recursive directory list before  and after the install and a diff of the two outputs to work out what it  installed.

See here:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Or, for the opposite effect:

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by ianc1 on 2011-06-28
Thanks FornatSeize.  No problems running Unity on this 3 year old machine.  And ~ is installed on its own partition.  However if I can install the kubuntu-desktop package and get the same effect I don't see any need or advantage in doing a fresh my kubuntu install.

Snowpine thanks for the links.  However I'm a little confused I thought apt-get remove only removed the package but left all its config files etc.

Thanks

---

### Post by snowpine on 2011-06-28
> **ianc1 said:**
> Snowpine thanks for the links.  However I'm a little confused I thought apt-get remove only removed the package but left all its config files etc.

Thanks

They aren't my tutorials but the author is a regular on these forums, I'm sure you can shoot him a PM if you have questions. :)

At any rate, even if you're right, an orphaned config file won't slow your system down in any way, just use a tiny bit of hard drive space I guess...

---

