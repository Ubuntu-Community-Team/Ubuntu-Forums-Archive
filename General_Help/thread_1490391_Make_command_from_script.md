---
title: "Make command from script"
date: 2010-05-22
forum: General Help
---

### Post by andypi on 2010-05-22
I've just downloaded the perl script texcount.pl. It is used to count the number of words in a LaTeX document.

At the moment, to use it I need to have a copy of the script wherever I want to run it. Is there some way I can turn it into a system-wide command such that without having to have a copy of the script to hand, I could just do something like "texcount doc.tex" in the terminal?

Thanks,

Andy

---

### Post by WorMzy on 2010-05-22
The best way (to my understanding) is to create a symbolic link in one of the /bin folders. /usr/local/bin is probably the best place to make the link, it's empty by default, so you won't accidentally overwrite anything.

```
sudo ln -s /path/to/the/script.pl /usr/local/bin/scriptname
```

I think that'll work. Afterwards, just run

```
scriptname <args>
```


Oh, almost forgot, you have to use the full path as the first argument for ln -s, not one relative to your current location. (e.g. "/home/username/Downloads/script.pl", _not_ "Downloads/script.pl")

---

### Post by wojox on 2010-05-22
You could move it to /bin since that directory should already be in your $PATH. 

If you want to use it exclusively you would create a /bin dir in your username directory, then add the path to .bashrc

---

### Post by blchinezu on 2010-05-22
> **andypi said:**
> I've just downloaded the perl script texcount.pl. It is used to count the number of words in a LaTeX document.

At the moment, to use it I need to have a copy of the script wherever I want to run it. Is there some way I can turn it into a system-wide command such that without having to have a copy of the script to hand, I could just do something like "texcount doc.tex" in the terminal?

Thanks,

Andy
  i think you can do that by alias or by linking to /usr/bin... 

try this:
make a file in **/usr/bin** called **textcount**, mark it as executable and insert this content:
> perl **/SCRIPT/PATH/**textcount.pl $@/SCRIPT/PATH/ obviously is _the path to the script_

it will work only if the script works in the current directory and doesn't need an absolute path.. if it needs an absolute path you'd better turn it into a nautilus script

---

### Post by gmargo on 2010-05-22
It is best not to put scripts in the /usr/bin/ directory.  Almost everything in the system goes here, so user scripts there amount to unmaintainable pollution.

The best practice is:

[LIST]
[*]For personal availability, put scripts in $HOME/bin/.
[/LIST]

[LIST]
[*]For general availability, put scripts in /usr/local/bin/.
[/LIST]
Both of these directories are already in your $PATH by default.  And don't forget about backing up /usr/local/.

---

### Post by jamesisin on 2010-05-22
Follow the suggestions of gmargo above.  In addition, you may benefit from this page:

[https://help.ubuntu.com/community/Nautilus_Scripts](https://help.ubuntu.com/community/Nautilus_Scripts)

It depends upon what your desired outcome is.

---

### Post by andypi on 2010-05-22
Thanks for all the suggestions.

I've only recently started using the terminal quite a bit (I had always seen it as a drawback of linux that you had to resort to it, whereas now I'm starting to see it as quite convenient).

Will have a play.

Andy

---

