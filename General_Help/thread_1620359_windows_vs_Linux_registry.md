---
title: "windows vs Linux registry?"
date: 2010-11-13
forum: General Help
---

### Post by choochoousmc on 2010-11-13
Most here know that windows uses a registry to track everything you do.
Sometimes clearing browser history does not clear the same and other info from the
registry.
Info that could be lying in wait to bite you in the butt later.
So a lot of registry cleaners are on the market.

so my question does Linux / Ubuntu have a similar registry?
 If so where is it located?
Is there a "cleaner"  / "fixer" for it?

---

### Post by Finalfantasykid on 2010-11-13
Most of the stuff that would require a registry, use config files instead in linux (text files, mostly in the etc folder and various others.  Gnome uses something called Gconf, which is pretty similar to a registry, but as far as I know, it is only used for Gnome related programs, not everything like the windows registry, so it inheritantly stays cleaner.

As far as cleaners, this isn't for that specifically, but it does do a great job at cleaning your hardrive.

```
sudo apt-get install bleachbit
```

---

### Post by choochoousmc on 2010-11-13
> **Finalfantasykid said:**
> Most of the stuff that would require a registry, use config files instead in linux (text files, mostly in the etc folder and various others.  Gnome uses something called Gconf, which is pretty similar to a registry, but as far as I know, it is only used for Gnome related programs, not everything like the windows registry, so it inheritantly stays cleaner.

As far as cleaners, this isn't for that specifically, but it does do a great job at cleaning your hardrive.

```
sudo apt-get install bleachbit
```

yep I got bleachbit already.
what does the command SUDO  mean?

---

### Post by bryangwilliam on 2010-11-13
sudo is a command that grants you elevated rights on your system. Type "man sudo" in your terminal to get a full description.

---

### Post by Habitual on 2010-11-13
> **choochoousmc said:**
> Most here know that windows uses a registry to track everything you do.
Sometimes clearing browser history does not clear the same and other info from the
registry.
Info that could be lying in wait to bite you in the butt later.
So a lot of registry cleaners are on the market.

so my question does Linux / Ubuntu have a similar registry?
 If so where is it located?
Is there a "cleaner"  / "fixer" for it?

gconf-editor and Computer Janitor
Be Careful.

---

### Post by Rubi1200 on 2010-11-13
Linux rarely accumulates the kind of "junk" you might be accustomed to in Windows.

I advise against using tools like Computer Janitor, Bleachbit, or Ubuntu Tweak as they can, and do, create more problems than they purportedly solve (for example, removing something they shouldn't!).

For general "cleaning" tips see here:
[http://ubuntuforums.org/showpost.php?p=800462&postcount=1](http://ubuntuforums.org/showpost.php?p=800462&postcount=1)

---

### Post by psusi on 2010-11-13
> **choochoousmc said:**
> Most here know that windows uses a registry to track everything you do.
Sometimes clearing browser history does not clear the same and other info from the
registry.
Info that could be lying in wait to bite you in the butt later.
So a lot of registry cleaners are on the market.

so my question does Linux / Ubuntu have a similar registry?
 If so where is it located?
Is there a "cleaner"  / "fixer" for it?

No, the registry does not "track everything you do".  It is where configuration settings are stored, not browser history.  No, Linux does not have a registry; it stores settings in config files in /etc.

---

### Post by 3Miro on 2010-11-13
Configuration files in /etc are global for the system. More configuration files are in /home/your_username, like browser history and other user specific settings. The files in home start with .something and to see them you need to hit Ctr + H in the file browser.

The windows registry is a database, so everything is loaded even if it is not used and when a program searches for its own key, it has to search among all other keys. If you have many programs installed, then they will slow down you computer even if you are not using most of them. Furthermore, if you install/remove programs, keys are left in the registry and this is one of the reasons why windows gets slower over time. Another problem with the database is that if it breaks, then the entire system breaks.

Advantages of separate configuration files:
- only files that are loaded are the ones that are used, so even if an uninstalled program leaves configuration files behind, the only effect that it will have is a few kilobytes of wasted HDD (not hit on performance)
- if a configuration file gets corrupt, then it only affects the corresponding program. This can still break the entire system, if the file belongs to a vital program (like compiz or gnome-panel), however, a regular program like a card game or a media player cannot affect the entire system.

Gconf-editor looks a lot like the windows registry, however, under the hood they have nothing in common. The only thing Linux that mimics a registry is the repository database, however, that is only associated with the process of installing and removing program. If you have 10 programs installed, program 11 will be installed faster, then if you have 100 programs and installing program 101. However, this only covers the installation itself, it has no effect on how fast the program is running afterwards. I think Computer Janitor keeps the software database clean.

---

### Post by psusi on 2010-11-13
> **3Miro said:**
> 
The windows registry is a database, so everything is loaded even if it is not used and when a program searches for its own key, it has to search among all other keys. 

No, this is not true any more than searching for a config file requires all files on the disk to be read.

> **3Miro said:**
> The only thing Linux that mimics a registry is the repository database, however, that is only associated with the process of installing and removing program. If you have 10 programs installed, program 11 will be installed faster, then if you have 100 programs and installing program 101. However, this only covers the installation itself, it has no effect on how fast the program is running afterwards. I think Computer Janitor keeps the software database clean.

The status of installed programs is stored in a plain text file that has nothing in common with the registry.  It is /var/lib/dpkg/status, and adding a new entry does not become any slower with more packages installed.

The only thing the computer janitor does related to packages is to delete the cache of downloaded packages in /var/cache/apt/archives.

---

### Post by PhilGil on 2010-11-13
> **psusi said:**
> No, the registry does not "track everything you do". It is where configuration settings are stored, not browser history. No, Linux does not have a registry; it stores settings in config files in /etc.
It's true that web browsing history is not housed in the registry, but many Windows programs do use it for dynamic storage of information such as recently opened documents.

> **psusi said:**
> The only thing the computer janitor does related to packages is to delete the cache of downloaded packages in /var/cache/apt/archives.
The last time I used Computer Janitor it functioned like *apt-get autoremove*, allowing you to uninstall packages that were dependencies of packages that were no longer installed on your system. It also had a nasty habit of wanting to remove every package that you installed using a .deb file. It's a risky program to use unless you know what you're doing.

The Configuration Editor is pretty slick. It's a graphical front end that consolidates information from the Gnome desktop configuration files in your home folder, and presents it in a way that makes changing settings simple and intuitive.

---

### Post by Monotoko on 2010-11-13
I find that Ubuntu generally takes care of itself with respect to configuration files and that I don't need to do any 'cleanups'. This is usually because it keeps global configuration files and user configuration files separate.

---

### Post by choochoousmc on 2010-11-27
ok everybody thanks. It's somewhat more clear.
However, in windows, I was doing a search in the registry.
I don't have it turned on now so generally.
In one of the H-key_classes etc etc .
The word I searched for came up as a folder under the domains folder.
It had about a 1,000 or so domains listed starting with a #1 and going to Z.
they were .com, .net, .org, .it, .de etc.
I never ever went to or searched for most of these websites.
Most were casino, gambling and porn related. My guess is these were pop ups or pop unders. And if you clicked too fast off center you could of clicked one of these hidden links.
anyway I am now in process of manually deleting all these undesirables.
That's why the original question.
I downloaded  Fslint and it did find some unusual addresses in Linux but only a few.

---

