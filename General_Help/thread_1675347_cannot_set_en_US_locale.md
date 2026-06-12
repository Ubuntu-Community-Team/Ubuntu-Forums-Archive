---
title: "cannot set en_US locale"
date: 2011-01-25
forum: General Help
---

### Post by draycor on 2011-01-25
I am new to Ubuntu but have been running opensuse for some time.  
I have installed Ubuntu 10.10x64 on an HP Envy 173D laptop and am having locale problems.  Here are some of the commands I have attempted:

attempt 1:
[INDENT]sudo locale -a
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_COLLATE to default locale: No such file or directory
C
POSIX
en_AG
en_AG.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NG
en_NG.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8

[/INDENT]
attempt 2:
[INDENT]sudo locale-gen en_US.utf8
Generating locales...
  en_US.UTF-8... up-to-date
Generation complete.

[/INDENT]
attempt 3: 
[INDENT]sudo dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "",
        LC_ALL = (unset),
        LANG = "en_US"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory                                                                      

Generating locales...                                                                                                                       
  en_AG.UTF-8... done                                                                                                                       
  en_AU.UTF-8... done                                                                                                                       
  en_BW.UTF-8... done                                                                                                                       
  en_CA.UTF-8... done                                                                                                                       
  en_DK.UTF-8... done                                                                                                                       
  en_GB.UTF-8... done                                                                                                                       
  en_HK.UTF-8... done                                                                                                                       
  en_IE.UTF-8... done                                                                                                                       
  en_IN.UTF-8... done                                                                                                                       
  en_NG.UTF-8... done                                                                                                                       
  en_NZ.UTF-8... done                                                                                                                       
  en_PH.UTF-8... done                                                                                                                       
  en_SG.UTF-8... done                                                                                                                       
  en_US.UTF-8... up-to-date                                                                                                                 
  en_ZA.UTF-8... done                                                                                                                       
  en_ZW.UTF-8... done                                                                                                                       
Generation complete.                   
[/INDENT]
Anyone know how to fix this issue?

Thanks,
draycor

---

### Post by gmargo on 2011-01-25
Don't know if this will help, but what is in your **/etc/default/locale** file?
```

$ more /etc/default/locale
LANG="en_US.UTF-8"

```

---

### Post by DanneStrat on 2011-01-25
Try this instead:

Go to system > administration > locale

There you can set your locale system-wide.

Hope this helps you!;)

---

### Post by draycor on 2011-01-25
> **gmargo said:**
> Don't know if this will help, but what is in your **/etc/default/locale** file?
```

$ more /etc/default/locale
LANG="en_US.UTF-8"

```
@gmargo
I get exactly what you posted:

more /etc/default/locale                                                                                                 
LANG="en_US.UTF-8"

---

### Post by draycor on 2011-01-25
> **DanneStrat said:**
> Try this instead:

Go to system > administration > locale

There you can set your locale system-wide.

Hope this helps you!;)
@DanneStrat:
My system does not have system > administration > locale.

It does have System > Administration > Language Support
This shows English (United States) followed by an English line.  I have Clicked the "Apply System-Wide" button, but it does not seem to change anything.

---

### Post by DanneStrat on 2011-01-25
> **draycor said:**
> @DanneStrat:
My system does not have system > administration > locale.

It does have System > Administration > Language Support
This shows English (United States) followed by an English line.  I have Clicked the "Apply System-Wide" button, but it does not seem to change anything.

You have to log out and back in again for the changes to apply.

---

### Post by draycor on 2011-01-25
> **DanneStrat said:**
> You have to log out and back in again for the changes to apply.
Thank you again, but that was tried.  I even repeated the sequence and then shutdown and restarted but still no luck.  

I thought that possibly my user was not configured right and was maybe not running the language support tool with sudo.  So I attempted the following in a terminal window:

sudo /usr/bin/gnome-language-selector 

(process:2638): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py:788: GtkWarning: gtk_cell_view_set_cell_data: assertion `cell_view->priv->displayed_row != NULL' failed
  cell = combo.get_child().get_cell_renderers()[0]
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_COLLATE to default locale: No such file or directory
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_COLLATE to default locale: No such file or directory

The lines about "No such file or directory" repeat many times.

---

### Post by gmargo on 2011-01-25
What files do you have under **/var/lib/locales/supported.d/**?  Is there anything strange in your .bashrc or .profile?

```

$ ls -l /var/lib/locales/supported.d/
total 8
-rw-r--r-- 1 root root 270 Oct  1 02:57 en
-rw-r--r-- 1 root root  18 Oct 22 18:07 local

$ more /var/lib/locales/supported.d/en
en_HK.UTF-8 UTF-8
en_DK.UTF-8 UTF-8
en_IN UTF-8
en_ZW.UTF-8 UTF-8
en_NZ.UTF-8 UTF-8
en_PH.UTF-8 UTF-8
en_NG UTF-8
en_US.UTF-8 UTF-8
en_GB.UTF-8 UTF-8
en_AU.UTF-8 UTF-8
en_SG.UTF-8 UTF-8
en_BW.UTF-8 UTF-8
en_AG UTF-8
en_ZA.UTF-8 UTF-8
en_CA.UTF-8 UTF-8
en_IE.UTF-8 UTF-8

$ more /var/lib/locales/supported.d/local
en_US.UTF-8 UTF-8

```

---

### Post by draycor on 2011-01-25
> **gmargo said:**
> What files do you have under **/var/lib/locales/supported.d/**?  Is there anything strange in your .bashrc or .profile?

```

$ ls -l /var/lib/locales/supported.d/
total 8
-rw-r--r-- 1 root root 270 Oct  1 02:57 en
-rw-r--r-- 1 root root  18 Oct 22 18:07 local

$ more /var/lib/locales/supported.d/en
en_HK.UTF-8 UTF-8
en_DK.UTF-8 UTF-8
en_IN UTF-8
en_ZW.UTF-8 UTF-8
en_NZ.UTF-8 UTF-8
en_PH.UTF-8 UTF-8
en_NG UTF-8
en_US.UTF-8 UTF-8
en_GB.UTF-8 UTF-8
en_AU.UTF-8 UTF-8
en_SG.UTF-8 UTF-8
en_BW.UTF-8 UTF-8
en_AG UTF-8
en_ZA.UTF-8 UTF-8
en_CA.UTF-8 UTF-8
en_IE.UTF-8 UTF-8

$ more /var/lib/locales/supported.d/local
en_US.UTF-8 UTF-8

```
Thanks for the suggestions.  I do not see anything unusual in the .profile or .bashrc.

Here are the results of the commands you suggested:

ls -l /var/lib/locales/supported.d/
total 8
-rw-r--r-- 1 root root 270 Oct  1 04:57 en
-rw-r--r-- 1 root root  18 Dec 16 09:16 local

$ more /var/lib/locales/supported.d/en
en_HK.UTF-8 UTF-8
en_DK.UTF-8 UTF-8
en_IN UTF-8
en_ZW.UTF-8 UTF-8
en_NZ.UTF-8 UTF-8
en_PH.UTF-8 UTF-8
en_NG UTF-8
en_US.UTF-8 UTF-8
en_GB.UTF-8 UTF-8
en_AU.UTF-8 UTF-8
en_SG.UTF-8 UTF-8                                                                                                                           
en_BW.UTF-8 UTF-8                                                                                                                           
en_AG UTF-8                                                                                                                                 
en_ZA.UTF-8 UTF-8                                                                                                                           
en_CA.UTF-8 UTF-8                                                                                                                           
en_IE.UTF-8 UTF-8                                                                                                                           

$ more /var/lib/locales/supported.d/local                                                                                  
en_US.UTF-8 UTF-8

---

### Post by eponymous alias on 2011-01-27
You're trying to use the en_US locale, but it doesn't exist on your machine.  The en_US.UTF-8 locale is a different locale.  To create the en_US locale, run:

# locale-gen en_US
Generating locales...
  en_US.ISO-8859-1... done
Generation complete.

and you should be good to go.

---

### Post by draycor on 2011-01-27
> **eponymous alias said:**
> You're trying to use the en_US locale, but it doesn't exist on your machine.  The en_US.UTF-8 locale is a different locale.  To create the en_US locale, run:

# locale-gen en_US
Generating locales...
  en_US.ISO-8859-1... done
Generation complete.

and you should be good to go.
Well that was easy.  Thank you, that seems to have fixed my problem.

---

### Post by beejee on 2011-01-28
I usually change it via Openoffice-Options-LanguageSettings menu, very straightforward and it seem to set the locale systemwide. 
That might be something nice to put in the preferences menu.

---

### Post by Paige.nicholls on 2011-02-14
> **draycor said:**
> @DanneStrat:
My system does not have system > administration > locale.

It does have System > Administration > Language Support
This shows English (United States) followed by an English line.  I have Clicked the "Apply System-Wide" button, but it does not seem to change anything.


The language support software should give you a button that says "Install/Remove Languages", if the English (United States) is already installed just re-install either in here (Mine gave me the option to install English package again even though it was already installed on my PC) or in a terminal window with the get-apt command as later directed in this forum Discussion.

However, as to the **_clicking that "Apply System-wide" button and it not responding_**, the software is set-up to only ask you for permission/confirm your changes once you've changed something. Mine didn't ask me to authenticate my system changes until I moved the English line above the English (United States) line and then moved it back to it's original position and clicked the "Apply System-Wide" button. It should ask for the same kind of authentication when installing/removing any locale packages in the same software, but not in the terminal window.

*Just a quick add-on tip for any new Ubuntu 10.10 users

---

