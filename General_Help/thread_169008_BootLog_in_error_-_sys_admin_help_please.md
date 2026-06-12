---
title: "Boot/Log in error - sys admin help please"
date: 2006-05-01
forum: General Help
---

### Post by cetol on 2006-05-01
Still being new to linux I have a problem I need a little help with. I introduced my daughter to ubuntu (erased MS win!!) on her pc. I think that she may have filled up her home directory with music. When trying to log on during boot-up I get an error message:

"GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case it is not possoble to log in. Please contact your system administrator"

The system will boot in recovery mode but I don't have a clue where to go from there.

I have accessed the home directory in recovery mode and she does have alot of music there. When I try to change directories though I cant.

 Please tell me how Ubuntu represents spaces in directory names.

Example: Music of the eighties :       is listed as a directory in /home/username. but when I try to cd to that directory exactly as show with spaces I get a no such file etc...

Any help is appreciated

---

### Post by Ramses de Norre on 2006-05-01
Music\ of\ the\ eighties (=> backslashes for every space)

---

### Post by Jason_25 on 2006-05-01
That works, but I use 'Music of the eighties' because it seems more logical.

---

### Post by Ramses de Norre on 2006-05-01
Ignore this..

---

### Post by dave9191 on 2006-05-01
Hey

You don't have to go all the way to recovery mode. When you boot normally, on the login screen you can hit Ctrl + Alt + F1, this will drop you to a virtual console. You can hit Ctrl + Alt + F7 to get back to the graphical interface. ( you can use this trick any time in linux :) ). This is prefarable then recovery mode for this, in recovery mode you are root and can delete something you might need by accident. This way you only delete what you are allowed to. 

Login with the account you wish to edit the files in. 

To navigate the command line:
```

cd dir_name  - will change to the directory named dir_name
cd .. - will go to the previous directory (parent dir)
rm file - will delete "file"
rmdir dir_name - will delete the directory dir_name as long as its not empty
rm -R dir_name - will delete the dir and everything in it (use carefully)


```

When typing in a file name, you can use the Tab button (above caps lock) to auto complete file names. So if you have a directory called "Holiday Snaps", you can type "cd Hol [TAB]" and it will autocomplete. 

Spaces on UNIX have to be escaped using the backslash, so "Holiday Snaps" would look like Holiday\ Snaps. You can also put the whole name in double quotes instead "Holiday Snaps". 

So you will either want 

cd "Music of the eighties" 
or 
cd Music\ of\ the\ eighties

and remember about the autocompletion with Tab, you can just type Music and autocomplete that. 

Hope that helps, 

--
Dave

---

### Post by vruum on 2006-05-01
I'm not sure it's a problem with space, but to check out the amount available and used, use the df command ```
 df /home/username 
``` if there's space left, it's a permission problem (maybe). go to the /home/username directory and type ```
 ls -la 
``` it will list all the files in the directory, and their properties the third column has the name of the user and the group the file belongs to, you will probably see that some of the files are owned by root, (the file is called .ICEauthority, I think)  so either change that or just delete the file. To change it type ```
 chown *username* .ICEauthority
``` if you're in a regular console (not recovery mode) prefix the above with sudo.

---

### Post by cetol on 2006-05-01
Thanks for the responses. I was able to log on and delete a few files and fix the problem. Seems she filled her entire drive with music from streamtuner..lol

Thanks again

C

---

