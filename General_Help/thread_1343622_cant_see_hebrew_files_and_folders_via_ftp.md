---
title: "cant see hebrew files and folders via ftp"
date: 2009-12-02
forum: General Help
---

### Post by tolaat01 on 2009-12-02
hi i got original xbox with folders and files in Hebrew. i use ubuntu 9.10 and windows xp at this computer and eeebuntu 3 nbr,xubuntu 9.10 on another computers.  when i ftp to the xbox using filezilla - i cant see the folders or the files that are in Hebrew. when i use jftp/gftp i can see the folders and files in gibberish. when i go to PLACES and connect to xbox via ftp i see the folders marked with error &quot;invalid encoding&quot;. i searched for this error in Google and saw a suggestion to install utf8-migration-tool - it didn't solve the problem.  i installed play on linux and than filezilla and now i can see the folders and files in gibberish.  when i access local ntfs partition in this computer i see Hebrew folders and files. when i access fillezilla via windows xp in this computer i can see Hebrew folders and files.  please advice

---

### Post by ed-koala on 2009-12-02
Sounds like your ftp program doesn't support the fonts needed to view Hebrew.  Don't know how to fix that though.

---

### Post by tolaat01 on 2009-12-02
> **ed-koala said:**
> Sounds like your ftp program doesn't support the fonts needed to view Hebrew.  Don't know how to fix that though.

hi thank u for the answer - however even from PLACES i get  gibberish and error regarding encoding - so i think it comes from ubuntu not from the program itself.

---

### Post by pbrane on 2009-12-02
If you know what the character set is named ( e.g., en_US.UTF-8 UTF-8 ) then you can set it in gFTP Preferences->Remote Character Sets.

Try **cat /var/lib/locales/supported.d/*** in a terminal. This should list the character sets you have installed.

[https://bugs.launchpad.net/ubuntu/+source/gftp/+bug/477462]("https://bugs.launchpad.net/ubuntu/+source/gftp/+bug/477462")

---

### Post by tolaat01 on 2009-12-04
hi 
thank u 4 the advice.
tried with file zilla and now at least i can see gibberish. 
tried on gftp - the program got unstable and and ubuntu got stuck for a while. 
i looked at the link u gave and i came to a link:

[http://docs.moodle.org/en/Table_of_locales](http://docs.moodle.org/en/Table_of_locales)
and used the instructions regarding ubuntu:
   **Ubuntu based**

  The default installation contains only limited number of locales. 

You can generate all locales on server from command line: 
      sudo ln -s /usr/share/i18n/SUPPORTED /var/lib/locales/supported.d/all
      sudo locale-gen
but the problem remains :(  .

---

### Post by pbrane on 2009-12-04
If I'm reading SUPPORTED right there are only two Hebrew character sets in there. Remember you have to have the REMOTE character set installed. I think you need to find out what the character set is that you are trying to view and somehow get that installed. At least that's what _should_ work. And of course make sure that both of those character sets you linked to are installed.

Have you installed **language-support-he** and **language-pack-he**? These packages appear to be what you need. It wouldn't hurt to look in the synaptic package manager and search for 'hebrew'. That is if you haven't already done all of this.

---

### Post by tolaat01 on 2009-12-04
hi
thank u 4 d suggestion.
it seems that  **language-support-he** wasnt installed but it didnt solve the problem.
i also use wine with filezilla and i get gibberish there too - didnt find where to change
the wine fonts.

---

### Post by tolaat01 on 2010-05-02
hi
installed fresh to ubuntu 10.04.
installed filezilla and in connection settings i used code ISO-8859-8.
problem solved.
didnt test in 9.04 or 9.10.
haim

---

### Post by tolaat01 on 2010-06-07
also tested and work on ubuntu 9.04 and 9.10

---

