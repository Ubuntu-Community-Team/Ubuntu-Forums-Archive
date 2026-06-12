---
title: "Installing PHP without Apache"
date: 2006-06-13
forum: General Help
---

### Post by dashifen on 2006-06-13
Greetings,

I wanted to know if there was an easy way to install PHP4 support without apache?  Synaptic wants to automatically install all of the apache packages but I've already installed and set up a different web server that I personally prefer.  I did it a while ago in Breezy somehow, but now I can't remember or reinvent what I did.

Thanks,
Dashifen

---

### Post by enopepsoo on 2006-06-13
[QUOTE=dashifen]Greetings,

I wanted to know if there was an easy way to install PHP4 support without apache?  Synaptic wants to automatically install all of the apache packages but I've already installed and set up a different web server that I personally prefer.  I did it a while ago in Breezy somehow, but now I can't remember or reinvent what I did.

Thanks,
Dashifen[/QUOTE]

You could leave the package management system and install it from php.net [http://www.php.net/downloads.php](http://www.php.net/downloads.php) maybe?[-X

---

### Post by dashifen on 2006-06-13
Obviously I could do that, however, compiling/configuring PHP while not impossible for me, isn't exactly what I'd call easy :D Thus, before I went that route, I figured I'd try to see if anyone else had any other suggestions.

---

### Post by finch on 2006-06-14
I 2 need php without apache how to install from package?
can u give a sample?
sory 4 stupid question

---

### Post by t3r0 on 2006-06-14
[QUOTE=dashifen]
I wanted to know if there was an easy way to install PHP4 support without apache?  
[/QUOTE]

Hi,

You can set the hold flag to Apache package with:

```

aptitude hold <name_of_unwanted_package>

```

And then install php4-* packages normally.. 


- Tero

---

### Post by lamego on 2006-06-14
Have you tried sudo apt-get install php4-cli ? This should install only the php4 command line interface.

---

### Post by lamego on 2006-06-14
Have you tried sudo apt-get install php4-cli ? This should install only the php4 command line interface.

---

