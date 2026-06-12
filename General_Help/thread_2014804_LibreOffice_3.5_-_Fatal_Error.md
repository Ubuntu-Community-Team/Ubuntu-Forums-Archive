---
title: "LibreOffice 3.5 - Fatal Error"
date: 2012-07-02
forum: General Help
---

### Post by philsweeney on 2012-07-02
Greetings,

12.04

After allowing updates I am getting this error with Libre Office (any app), when I try to open a file:

LibreOffice 3.5 - Fatal Error

The application cannot be started. 
[/home/phil/.config/libreoffice/3/user/extensions/shared/extensions.db] Berkeley Db error (0): Db::open: Permission denied.

I uninstalled Libre Office and re-installed via Ubuntu Software Center and I am still getting that error message. I checked permissions on the shared folder any everything seems OK.


Any help would be appreciated.

---

### Post by vasa1 on 2012-07-02
> **philsweeney said:**
> Greetings,

12.04

After allowing updates I am getting this error with Libre Office (any app), when I try to open a file:

LibreOffice 3.5 - Fatal Error

The application cannot be started. 
[/home/phil/.config/libreoffice/3/user/extensions/shared/extensions.db] Berkeley Db error (0): Db::open: Permission denied.

I uninstalled Libre Office and re-installed via Ubuntu Software Center and I am still getting that error message. I checked permissions on the shared folder any everything seems OK.


Any help would be appreciated.
Exit LibreOffice and make sure that no libreoffice process is running. At least you should not see soffice.bin running. Then, rename /home/phil/.config/**libreoffice** to /home/phil/.config/**libreoffice_bak**. Now start LibreOffice. If the only problem was a corrupt profile, it will recreate your profile. I'm assuming you haven't invested too much effort in creating styles or templates or whatever else but all that stuff will now be in the libreoffice_bak folder and you could slowly move stuff back watching all the while for breakage. This assumes of course that making an new profile as described above allows LibreOffice to start.

If you still need help, you could ask over here: [http://ask.libreoffice.org/questions/](http://ask.libreoffice.org/questions/)

---

### Post by philsweeney on 2012-07-02
> **vasa1 said:**
> Exit LibreOffice and make sure that no libreoffice process is running. At least you should not see soffice.bin running. Then, rename /home/phil/.config/**libreoffice** to /home/phil/.config/**libreoffice_bak**. Now start LibreOffice. If the only problem was a corrupt profile, it will recreate your profile. I'm assuming you haven't invested too much effort in creating styles or templates or whatever else but all that stuff will now be in the libreoffice_bak folder and you could slowly move stuff back watching all the while for breakage. This assumes of course that making an new profile as described above allows LibreOffice to start.

If you still need help, you could ask over here: [http://ask.libreoffice.org/questions/](http://ask.libreoffice.org/questions/)

Great! That did it! Thanks. Moved my templates and back in business.

---

