---
title: "Installing stardict dictionaries."
date: 2010-09-10
forum: General Help
---

### Post by RabbitWho on 2010-09-10
Hi guys. 

I need an offline Spanish-english english-spanish dictionary. 

I've read other threads about stardict and have done what they say but I  must be doing something fundamentally wrong because it's just not  working. 

Here are the instructions: [B]
  
 Install Dictionaries in Linux:                                                                    To install these tarball                           dictionaries, do this:                                                                    tar -xjvf a.tar.bz2                                                                    mv a /usr/share/stardict/dic[/B] 

I download a dictionary file, move it where  I'm supposed to move it. No change. 

Can anyone link me to a Spanish dictionary for stardict they know actually works? 

Alternatively any other offline dictionary program with a Spanish  dictionary that's gonna be easy (or just possible) to get working.. any ideas for me?

---

### Post by luigi_mb on 2010-09-10
Did you unpack the archive? 

```

tar -xjvf [dictionary].tar.bz2 

```

and moved the .dz , .idx and .ifo files to /usr/share/stardict/dic ?


/luigi

---

### Post by RabbitWho on 2010-09-10
As I said in my first post, yes I did that.

---

### Post by RabbitWho on 2010-09-19
bump?

---

### Post by hrickh on 2010-09-19
When you unpacked your dictionaries, did you keep them in their respective unpacked directories, then move the directories into /usr/share/stardict/dic? That's the way mine are set up.

Also, when you run Stardict, what do you see when you click on "Manage dictionaries"?

R.
==

---

### Post by cgb223 on 2011-01-23
Bump for the Spanish dictionary link or other good program alternative

---

