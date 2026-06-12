---
title: "Auto character return"
date: 2009-07-22
forum: General Help
---

### Post by Tarmael on 2009-07-22
Hey guys,

I'm at work at the minute.

I've just set up an old firewall to be recycled into being a live monitor feed of all the different computers in the domain.

What it does is it shows the status of all the different computers. It does this by connecting to a web server with your browser. The service that's being ran is 'whatsup'.

So my question is:

Is there a way to automate a single character return on startup.

So far I have it set to open firefox and connect to the server, it's just that you need to login for it to work.

If I can manage to get it to automate the enter key stroke when I log in after say, 20 seconds, then it will log into whatsup and all I need to do of a morning is press the power button.

Thanks in advanced!

Tarmael

---

### Post by Tarmael on 2009-07-22
scrap that, got it working.

Here's what I did:

installed xmacro!

installed that. Macro I have is called <b>enter.macro</b>
```
KeyStrPress Return
KeyStrRelease Return
```


Couple that with a python script I made.

login.py

```
import time, os

time.sleep(20)
os.system("cat enter.macro | xmacroplay -d 100 :0")
```



Then I added the scripts to started.

python login.py

and

firefox IPADDRESS

Now it's an automated kiosk like machine.

I'm also using the firefox addon: Full Fullscreen 3.3

Thanks for reading~!

Tarmael

---

