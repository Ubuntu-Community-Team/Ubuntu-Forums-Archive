---
title: "unrar ERROR: Unknown option: ?"
date: 2012-10-11
forum: General Help
---

### Post by r00tuuu123 on 2012-10-11
Hi all I'm trying to unrar some files in Ubuntu 10.04/Backtrack5r2 and am getting  a persistent error message. 
Example: ERROR: Unknown option: root@bt:~/Downloads/aquateens# unrar x 92 - Baffler Meal.rar  
I have tried several files using this command

 unrar x 92 - Baffler Meal.rar 
I have tried the e,l,a and --extract options and a few others but still get the 

 ERROR: Unknown option: root@bt:~/Downloads/aquateens# unrar x 92 - Baffler Meal.rar  
Message is my command correct as  unrar x 92 - Baffler Meal.rar
When I type unrar I get the list of options but even with the applicable  ones I still get error.  Any help?

---

### Post by drmrgd on 2012-10-11
I don't use unrar as much as other utilities, so I might be a little off here.  But, your syntax doesn't quite look right to me, especially after having a look at the man pages.  I think you need to remove the '-' after '92' as the rar'd file should be passed as an option to unrar. 

I'm also wondering about the '92' part.  Are you intending that as the path to extract the file to, or is that supposed to be a file in the archive that you want to skip (and thus, you should use '-x' not just 'x' according to the man pages)?  If you intend '92' to be the path, the 'x' option in combination with '92' is going to cause an error I think.  

Maybe a quick explanation of how you want to unrar that file would be helpful.

---

### Post by Azdour on 2012-10-11
Hi,

92 - Baffler Meal.rar 

If this is the name of the rar file you are trying to extract then I would recommend trying quotes:

unrar x "92 - Baffler Meal.rar"

It may be that unrar is parsing the the unquoted filename as parameters/options.

---

### Post by sandyd on 2012-10-11
> **r00tuuu123 said:**
> Hi all I'm trying to unrar some files in Ubuntu 10.04/Backtrack5r2 and am getting  a persistent error message. 
Example: ERROR: Unknown option: root@bt:~/Downloads/aquateens# unrar x 92 - Baffler Meal.rar  
I have tried several files using this command

 unrar x 92 - Baffler Meal.rar 
I have tried the e,l,a and --extract options and a few others but still get the 

 ERROR: Unknown option: root@bt:~/Downloads/aquateens# unrar x 92 - Baffler Meal.rar  
Message is my command correct as  unrar x 92 - Baffler Meal.rar
When I type unrar I get the list of options but even with the applicable  ones I still get error.  Any help?
Linux doesn't like spaces in filenames - you need to either

a) Escape it with a slash \
b) use Quotes.

```

unrar e "92 - Baffler Meal.rar"

```

---

### Post by r00tuuu123 on 2012-10-11
Thanks Sandyd It was the quotes. Even though the way the file was posted is the real file name.

---

### Post by foxmulder881 on 2012-10-11
And remember to use ```
unrar e
``` and not ```
unrar x
```

---

