---
title: "init.d startup script"
date: 2010-10-24
forum: General Help
---

### Post by Hippytaff on 2010-10-24
I have a startup bash script to give the user options at startup (launch firefox etc), however it causes ubuntu to hang on the loading screen with red things at startup. I dropped into command line and removed it, so that is definitely the problem. The script works...does anyone know if having a startup script in init.d can open a terminal to interact with the user, and why this script causes ubuntu to be unable to startup?

---

### Post by Brandon Williams on 2010-10-27
When you say "open a terminal", what do you mean? You won't be able to open an xterm, and it would be unusual (though not completely unheard of) to run an interactive command from an /etc/init.d script, so I'm not certain exactly what is necessary in order to do so.

What exactly does your init.d script look like? It would be easier to give you useful information about the nature of your problem if we knew precisely what you're trying to do.

---

### Post by Hippytaff on 2010-10-27
Heres the script

```

#!/bin/bash
#choose between peppa pig dvd and evening usage
echo "Want shall I do, 1, peppa pig or 2, firefox: ''"
read ans
if [[ $ans == '1' ]]; then
totem dvd://
elif [[ $ans == '2' ]]; then
firefox
else 
echo "ok"
fi 

```It wouldn't be the first time I tried to do something that either can't be done or would be silly to do :-)

To explain, it's for my daughter to be able to press 1 and get her peppa pig dvd running :-)

---

### Post by Brandon Williams on 2010-10-28
Do you have the system configured for automatic password-less login? If so, then I think you will have more luck adding this functionality as a startup application to run at login.

Also, have you considered generating a dialog for her instead of requiring keyboard input? Something like:
```
#!/bin/sh
if zenity --question --text="Play peppa pig DVD?"
then
    exec totem dvd://
fi
```
That way, she just has to press enter during automatic login.

---

### Post by Hippytaff on 2010-10-28
All the users require passwords, but might set up an account that doesn't and use your suggestion...thank you very much - a fresh pair of eyes :-)

---

