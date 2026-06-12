---
title: "Making your own desktop applications in Ubuntu?"
date: 2010-06-19
forum: General Help
---

### Post by theio_vrefos on 2010-06-19
Are there any tutorials for this? My sister wants a really easy application that pops a random quotation every time she presses on an icon (probably appearing in the panel). I'm fairly experienced in programming, but i've never done desktop apps for ubuntu.

---

### Post by twisted_steel on 2010-06-19
I would look into capturing the output from the 'fortune' program.  You can probably restrict it to quotations only.  Once you do that, you could display the output via some sort of Gtk window (via perl, python, C, etc.), or you could just use 'zenity'.  Zenity makes it extremely easy to create a quick window.  Check out 'man zenity' for more information.

For example, the command 'zenity --info --text=Hello' will give you a little popup window.

Here is a quick example in bash.

```

#!/bin/bash

output=`fortune`

zenity --info --text="$output"

```

Save the file to something like 'test.sh' and give it executable permissions with 'chmod u+x test.sh'.  Then run it from the command line with './test.sh' or you should be able to double-click it and select 'Run'.

As far as creating a shortcut, these are done with .desktop files and you should be able to make your own by right-clicking on an empty area of the Desktop and selecting Create Launcher.  You will need to browse for whatever program you created as the command.

---

### Post by twisted_steel on 2010-06-19
You can find more data files for the fortune program if you search for 'fortune' in Synaptic package manager.  Also, 'cowsay' is always worthwhile if you want to print out something via the command line.

From a terminal window, try:
```
fortune | cowsay
```

This will take the output of fortune and send it to cowsay, which will display a talk bubble with the fortune inside.  You can also find more things to "speak" by looking in /usr/share/cowsay/cows.  This way, you can have a turtle show up instead with

```
fortune | cowsay -f turtle
```

---

### Post by theio_vrefos on 2010-06-19
Thank you very much for the answers :D

I made it with a custom launcher and the fortune program, using your BASH script. I tried to add cowsay to the mix, as she would love cows, but unfortunately zenity messes up the alignment. 

I also added some custom quotations to the fortune application. Is there any way to make quotations in another language (greek)?

---

### Post by twisted_steel on 2010-06-20
> **theio_vrefos said:**
> Thank you very much for the answers :D

I made it with a custom launcher and the fortune program, using your BASH script. I tried to add cowsay to the mix, as she would love cows, but unfortunately zenity messes up the alignment. 

I also added some custom quotations to the fortune application. Is there any way to make quotations in another language (greek)?

Glad to see it is working.

As far as fortunes in Greek, I have not found any.  You could take a look at some of the other language files out there to get an idea of how to set them up.  There are packages such as: fortunes-br, fortunes-de, and fortunes-es (Portuguese, German, and Spanish, respectively).  I think 'gr' would be the Greek letter code.

---

