---
title: "flash player"
date: 2010-05-21
forum: General Help
---

### Post by doronlevie on 2010-05-21
[FONT=Trebuchet MS][SIZE=2]hello, i'm new to these forums :)
I have been using linux almost a year by now and was satisfied the whole  time. I downloaded the new Ubuntu release lately and currently have one  main problem which I can't wait to it's solution much longer. Flash  player doesn't work. it seems like it's not even going to work... [/SIZE][/FONT][FONT=Trebuchet MS][SIZE=2][COLOR=#000000]I'm an officer  in the army, gotta work with my computer on documents and other things  that flashplayer is critical for their function. I don&#8217;t have any  alternative to using my current computer, therefore I have to have this  working on my Ubuntu as soon as possible.[/COLOR][/SIZE][/FONT][FONT=Trebuchet MS][SIZE=2] when I  had the karmic koala release flash worked just fine.
I saw and tried everything from shayli147's thread, nothing helped.

1. is there a way to solve this bug?[/SIZE][/FONT] [FONT=Trebuchet MS][SIZE=2]
2. if not yet, I would like to return to the karmic koala release. how  do I do so?

I have to have this problem solved. it sounds tiny but it's more than  important. [/SIZE][/FONT] [FONT=Trebuchet MS][SIZE=2]:)[/SIZE][/FONT]

---

### Post by LowSky on 2010-05-21
1. Are you sure flash is installed?
The easiest thing to do is to open termnial and type
```
sudo apt-get install flashplugin-nonfree
```

2. There isn't an easy way to go back. You would have to reformat your hard drive and reintall the older version. If you have to do this, but there shouldn't have to, first backup all your data.

---

### Post by doronlevie on 2010-05-21
[FONT=Trebuchet MS][SIZE=2][COLOR=#000000]i just  tried what you mentioned. it didn't work, but the following message  appeard:
[/COLOR][/SIZE][/FONT][FONT=Trebuchet MS][SIZE=2]"Apt Authentication issue

Problem during package list update. The package list update failed with a  authentication failure. This usually happens behind a network proxy  server. Please try to click on the "Run this action now" button to  correct the problem or update the list manually by running Update  Manager and clicking on "Check".[/SIZE][/FONT] [FONT=Trebuchet MS][SIZE=2]"

[/SIZE][/FONT]  [FONT=Trebuchet MS][SIZE=2][COLOR=#000000]when i  followed the instructions, another problem occurred:
[/COLOR][/SIZE][/FONT][FONT=Trebuchet MS][SIZE=2]"An error occurred

The following details are provided:[/SIZE][/FONT] [FONT=Trebuchet MS][SIZE=2]

W: A error occurred during the signature verification. The repository is  not updated and the previous index files will be used.GPG error: [/SIZE][/FONT] [FONT=Trebuchet MS][SIZE=2][http://download.virtualbox.org]("http://download.virtualbox.org/")  lucid Release: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY 54422A4B98AB5139

W: Failed to fetch [/SIZE][/FONT] [FONT=Trebuchet MS][SIZE=2][http://download.virtualbox.org/virtualbox/debian/dists/lucid/Release](http://download.virtualbox.org/virtualbox/debian/dists/lucid/Release)[/SIZE][/FONT]   [FONT=Trebuchet MS][SIZE=2]

W: Some index files failed to download, they have been ignored, or old  ones used instead.[/SIZE][/FONT] [FONT=Trebuchet MS][SIZE=2]"

[/SIZE][/FONT]  [FONT=Trebuchet MS][SIZE=2][COLOR=#000000]could  this be the source of the problem?
  
  
p.s. i have virtual box installed, [/COLOR][/SIZE][/FONT][FONT=Trebuchet MS][SIZE=2][COLOR=#000000]but i didn't understand what  it has to do with the message. is there something i need to do with it?[/COLOR][/SIZE][/FONT]

---

### Post by shayli147 on 2010-05-22
[SIZE=1]hi, i've run into the same problem and the following thread has the solution:
[http://ohioloco.ubuntuforums.org/showthread.php?p=9331862 ]("http://ohioloco.ubuntuforums.org/showthread.php?p=9331862")[/SIZE] [SIZE=1]

it helped me, i hope it helps you too [/SIZE] [SIZE=1]:)
[SIZE=4]
sorry, don't know how to delete this, the full message is the one below this one ^^"[/SIZE]
[/SIZE]

---

### Post by shayli147 on 2010-05-22
> **doronlevie said:**
> [FONT=Trebuchet MS][SIZE=2]

W: A error occurred during the signature verification. The repository is  not updated and the previous index files will be used.GPG error: [/SIZE][/FONT] [FONT=Trebuchet MS][SIZE=2][http://download.virtualbox.org]("http://download.virtualbox.org/")  lucid Release: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY 54422A4B98AB5139

[/SIZE][/FONT]

hi,
regarding the error message mentioned above you've been getting,
i've run into the same problem and the following thread has the  solution:
[http://ohioloco.ubuntuforums.org/showthread.php?p=9331862  ]("http://ohioloco.ubuntuforums.org/showthread.php?p=9331862")

it helped me, i hope it helps you too :)

---

