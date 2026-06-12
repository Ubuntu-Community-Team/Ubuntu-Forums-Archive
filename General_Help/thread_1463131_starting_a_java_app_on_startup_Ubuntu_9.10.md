---
title: "starting a java app on startup Ubuntu 9.10"
date: 2010-04-26
forum: General Help
---

### Post by Tekken on 2010-04-26
First of all I'm using Ubuntu 9.10.

I have tried using System/Preferences/Startup Applications
I added:

java -Xint -cp /home/Edgar/dist/Edagr.jar:/home/Edgar/dist/Annotator.jar com.ionetrics.edgar.Edgar

I don't know if I am calling this incorrectly or not. I know that I can call this from a terminal and it will run correctly. However it will not run at startup. I have added Teamviewer to startup and it runs properly. 

Thanks for your input in advanced.

---

### Post by Brandon Williams on 2010-04-27
Look in your ~/.xsession-errors file to see if there are any useful error messages. My guess is that there is something in your shell environment within the terminal that is not initialized correct in the startup environment, and some message in ~/.xsession-errors should give you an indication of what it is.

---

