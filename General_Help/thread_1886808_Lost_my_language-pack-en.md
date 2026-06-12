---
title: "Lost my language-pack-en"
date: 2011-11-25
forum: General Help
---

### Post by Merung on 2011-11-25
My computer froze while I was doing a 'sudo apt-get upgrade' about a week ago.  It appears it was in the middle of upgrading language-pack-en, because when I tried to resume after a reboot, I was told:

```
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 language-pack-en : Depends: language-pack-en-base (>= 1:11.10+20111006) but it is not installed
E: Unmet dependencies. Try using -f.

```

I ran 'sudo apt-get -f install' and received:

```
After this operation, 5,439 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: error processing language-pack-en (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 language-pack-en
E: Sub-process /usr/bin/dpkg returned an error code (1)

``` 

Unfortunately at the time, I did not know about the --remove option, and so figured I would do it manually.  I did a 'sudo apt-get remove <list of 4 language packs (language-pack-en, language-pack-en-base, and 2 others)>

After this completed, the "2 others" were removed, language-pack-en and en-base are in completely inoperable states, and I am stuck in a loop with the commands apt-get tells me to run to fix the problem.

When I returned home from my business trip, I logged into gnome and received a pop-up telling me that my language is no longer valid, and do I want to rename my directories to the new language.  I told it to skip the renames.

Here is the full text of what I am seeing:

```

merung@khellendros:~/newBT/Seeding$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 language-pack-en : Depends: language-pack-en-base (>= 1:11.10+20111006) but it is not installed
E: Unmet dependencies. Try using -f.

merung@khellendros:~/newBT/Seeding$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  language-pack-en language-pack-en-base
The following NEW packages will be installed:
  language-pack-en-base
The following packages will be upgraded:
  language-pack-en
1 upgraded, 1 newly installed, 0 to remove and 40 not upgraded.
1 not fully installed or removed.
Need to get 0 B/798 kB of archives.
After this operation, 5,439 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: error processing language-pack-en (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 language-pack-en
E: Sub-process /usr/bin/dpkg returned an error code (1)

merung@khellendros:~/newBT/Seeding$ sudo apt-get --reinstall install language-pack-en
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 language-pack-en : Depends: language-pack-en-base (>= 1:11.10+20111025) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Thank you for any help!  Until this is resolved I cannot do any other package maintenance either.

---

### Post by Merung on 2011-11-27
Does anyone have any info or ideas on this? /beg

---

### Post by Merung on 2011-11-30
wow... No one has any ideas?

---

### Post by cholericfun on 2011-11-30
hi
i'm just browsing through the man-pages
```
apt-get -f install
``` is trying to fix things. Sounds silly but did you try a simple ```
apt-get install
```?


have a look at dpkg
i'm not in the mood to brake my system to try things out at the moment (what makes me think you are i don't know...). Just to say i'm not entirely sure about the following. Good thing is there is a ```
--no-act | --dry-run | --simulate
``` option

the man for dpkg also has this wonderful command
```

 remove-reinstreq:  Remove  a  package, even if it's broken
              and marked to require reinstallation. This may, for  exam&#8208;
              ple,  cause  parts of the package to remain on the system,
              which will then be forgotten by dpkg.

```


so all in all stuck together try this:

```
dpkg --simulate --force-remove-reinstreq language-pack-en
```

if the output doesnt look to bad then try removing it (i.e. not simulating)


hope this is of any  use

---

### Post by Merung on 2011-11-30
You are my hero!  that worked... I had to add -r to the command, but that allowed me to force the remove of the package.  Once that was finished, I reinstalled it and was able to perform the system maintenance I needed to do.

Thank you much!

---

### Post by cholericfun on 2011-11-30
cool, glad that worked,

just for other peoples benefit: is that what you used?

```
dpkg -r --force-remove-reinstreq insertpackagenamehere
```

---

### Post by Merung on 2011-11-30
```

merung@khellendros:~$ sudo dpkg --force-remove-reinstreq -r language-pack-en
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 362310 files and directories currently installed.)
Removing language-pack-en ...
Processing triggers for software-center ...
INFO:softwarecenter.db.update:no translation information in database needed

```

After I ran that, I re-installed language-pack-en and its dependencies. Once that was complete, everything else I needed to do worked.

---

