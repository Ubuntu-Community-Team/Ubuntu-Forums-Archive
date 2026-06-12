---
title: "Vital system configuration files - how to find them ?"
date: 2009-07-12
forum: General Help
---

### Post by credobyte on 2009-07-12
I'm not sure where I should post this, so .. let's start from here ( General Help ) :)
I've spent some time on developing some kind of System Restore application but I've one problem - where I can find all vital system configuration files ( desktop, driver configuration, etc. ) ? Finding all .config files is a piece of cake, but files without an extension needs to be added manually.

Any suggestions ? Where I could get such an information ?

---

### Post by Ocxic on 2009-07-12
most of the system configuration files will be located in /etc.

---

### Post by credobyte on 2009-07-12
> **Ocxic said:**
> most of the system configuration files will be located in /etc.

Um, yes, but going through all files located in /etc would be insane ( as previously said, many of them have no extension ). Is there a way to find out, which ones are currently loaded/being used ?

---

### Post by Ocxic on 2009-07-13
Well if there is a file in /etc it will be used, generally the only files in that directory not being used would be from packages/applications that have been un-installed and have not had there configuration files removed. 

If you looking for something specific i would check the documentation for the program that your trying to backup the settings for, sometimes the config file will contain the name of the application your backing up.
The /etc directory is fairly small, you might consider backing up the entire directory. but that will depend on your backup model that your trying to implement.

Don't forget that a lot of configuration settings for applications will be contained within a users home directory.

---

### Post by credobyte on 2009-07-13
Ok, thank you :) 45Mb is fairly small size for the whole /etc backup - will check it out a bit later on today !

---

