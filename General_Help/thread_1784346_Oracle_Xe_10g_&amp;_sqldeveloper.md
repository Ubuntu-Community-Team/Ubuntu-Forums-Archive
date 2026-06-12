---
title: "Oracle Xe 10g &amp; sqldeveloper"
date: 2011-06-16
forum: General Help
---

### Post by GodveX on 2011-06-16
im trying to install these two files and could only find a tutorial for linux 10 and im using linux 11.04 natty does anyone know of a guide i can use since im still new with this version of linux please ?

or would it be easier to switch to linux 10 in order to use these programs due to compatibility issues?

i installed oracle xe but it wouldnt even load the home page to access the databases and i have no idea how to install .rpm files with alien i tried but given up :o 

terminal code for alien i used:
cd ~/Desktop
{error showed to log in root or fakeroot}
su - 
{entered root pass}
alien -k sqld.rpm 
{cannot find package}

thats all i could get from alien :P

sorry for the brick wall of text guys

---

### Post by GodveX on 2011-06-16
i kept on trying and finally installed oracle xe it is working to the full on linux only problem left is how to install an rpm file properly i know if i open terminal and drag the sqldeveloper.sh there it will open but i wish to install it any help please ?

---

### Post by GodveX on 2011-06-16
after another hour of research i finally got the hang of alien all i needed to do was 

```
sudo alien --script -k <file_name>.rpm
```

and then to install 

```
sudo dpkg -i <file_name>.deb
```

and since my files were currently on the desktop i had to also use cd ~/Desktop so that terminal will know that what files i need are all on the desktop hopes this can help another noobie just like myself

---

