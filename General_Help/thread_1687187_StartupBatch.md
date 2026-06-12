---
title: "Startup/Batch?"
date: 2011-02-13
forum: General Help
---

### Post by Hosmion on 2011-02-13
Hello everyone :).  Been a while since I've been on these forums.  Been doing a lot of heavy gaming on my Windows system.  Now that I'm back to Ubuntu, I have a couple questions.

1)  Is there like a system command language (For example, Batch on Windows) that controls the terminal and can open the internet?  I need a reminder sort of thing to happen that checks the price of something as it goes up and down, so every time I turn on my computer I want it to be able to open up Chrome or Firefox or something to the webpage that shows me the current price.  Is there a language that does this in terminal?

2)  Is there like a sort of start up folder that every time I boot my Ubuntu partition the program (as above) is executed so I am reminded?

Thanks,
~Lenni

---

### Post by An Sanct on 2011-02-13
Well for the terminal automation, you can use bash
```
https://help.ubuntu.com/community/Beginners/BashScripting
http://www.ubuntugeek.com/download-bash-shell-scripting-guide-for-beginners-pdf.html

```

You can set startup applications through system -> preferences -> startup applications

For terminal downloading use **wget**
```
http://freshubuntu.blogspot.com/2006/10/ubuntu-tips-and-wget.html
```

You are free to create your own script, that will download the desired page, parse it and alert you...

---

### Post by Hosmion on 2011-02-13
> **An Sanct said:**
> Well for the terminal automation, you can use bash
```
https://help.ubuntu.com/community/Beginners/BashScripting
http://www.ubuntugeek.com/download-bash-shell-scripting-guide-for-beginners-pdf.html

```

You can set startup applications through system -> preferences -> startup applications

For terminal downloading use **wget**
```
http://freshubuntu.blogspot.com/2006/10/ubuntu-tips-and-wget.html
```

You are free to create your own script, that will download the desired page, parse it and alert you...

Thank you sooo much!  It worked!

---

