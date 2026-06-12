---
title: "look for a way to print all modules installed"
date: 2010-06-30
forum: General Help
---

### Post by blackhawx on 2010-06-30
Is there a way with Ubuntu to print out a list of all the modules that I installed on top of the original Ubuntu package.  This way if my system ever crashes I'm not spending days to put back on what I had installed prior?

Even if this process if not fully for the system and for smaller sections, like a list of the games I have installed, or a list of all the Internet, office, sound applications installed, etc..
that would be fine too.

thanks!

---

### Post by gzarkadas on 2010-06-30
Open a terminal window and type the following command (better copy it from here and paste it with Ctrl+Shift+V in the terminal).

It will create a file named `additional-packages inside your home folder with the names of all packages that are installed by you.

```

cat /var/lib/dpkg/status | awk 'BEGIN{RS="";FS="\n";OFS="\n"} { pkg=substr($1,10,length($1)); prio=""; for (i=2;i<NF;++i){ if ($i~/Priority: /){ prio=substr($i,11,length($i)); break }}; if (prio == "optional" || prio == "extra") print pkg }' > ~/additional-packages

```

The command feds the contents of `/var/lib/dpkg/status' (where info about the installed packages is held) to an awk script, the output of which is redirected to the file mentioned above. The awk script scans each multiline record of the input for packages with priority `optional' or `extra'. Packages with these priorities are those installed after the system installation.

When you will try to reinstall in the future, use the liveCD to make the default install and then copy the file again to your home folder, open a terminal window and type:
```

sudo apt-get install $(cat ~/additional-packages)

```

---

### Post by blackhawx on 2010-06-30
thank you so much for that tip! will give it a shot tonight with the first tip you mentioned.  as far as the 2nd tip you mentioned, what file are you talking about when you say...

```

...copy the file again to your home folder...

```

and what is the benefit?

thanks again!

---

### Post by gzarkadas on 2010-07-01
The command I mentioned creates a text file in your home directory. Since you want to have the list for re-installation, you 'll backup this file. 

In the event of a re-install chances are that you'll end up with a clean system and thus with an empty home folder. So, you 'll need to copy the backup of the file back to its location (empty home folder). 

If you do so, then you can automatically reinstall all additional packages with the single command mentioned at the second part of my post (and that's the benefit: automation :p).

---

### Post by justleen on 2010-07-01
why not used dpkg --get-selections to get the state of all packages?

```

dpkg --get-selections > package-list
# to restore:
dpkg --set-selections < package-list
apt-get dselect-upgrade


```

---

### Post by artemyv on 2010-07-01
> **justleen said:**
> why not used dpkg --get-selections to get the state of all packages?



Or if you prefer the GUI way - In the Synaptic Package Manager -Menu File - Save Markings/Read Markings

---

### Post by gzarkadas on 2010-07-01
> **justleen said:**
> why not used dpkg --get-selections to get the state of all packages?

Primarily, is a matter of taste :); as a second -logical this time- argument, because `all' is not in specs here: the original question excludes the default-installed packages. Thus one has to match against package priority and therefore scan /var/lib/dpkg/status.

It is true that the solution I posted does not distinguish between installed and deinstalled packages, but in a new system this is not usually of a difference. In any case this information can also be extracted from /var/lib/dpkg/status, though the awk script has to grow a bit:

```

cat /var/lib/dpkg/status | awk '
BEGIN{
    RS="";FS="\n";OFS="\n"
}
{ 
    pkg = substr($1,10,length($1))
    prio = ""
    found = 0
    for (i=2; i<NF && found < 2; ++i)
      {
        if ($i~/Status: /)
          {
            if (substr($i,11,length($i)) == "install ok installed")
                ++found
            else
                break
          }
        if ($i~/Priority: /)
          {
            prio=substr($i,11,length($i))
            ++found
          }
      }
    if (found == 2 && (prio == "optional" || prio == "extra"))
        print pkg
}'  > ~/additional-packages 

```

---

