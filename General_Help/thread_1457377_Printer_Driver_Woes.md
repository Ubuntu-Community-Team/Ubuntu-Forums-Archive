---
title: "Printer Driver Woes"
date: 2010-04-18
forum: General Help
---

### Post by LittleFrank on 2010-04-18
I'm new to Linux (Ubuntu) and trying to install a printer driver.

I have a Samsung SCX 4826FN for which Samsung provides a Linux "Unified Driver"along with vague instructions for installing it. 

Those instructions tell me to Open "Root Terminal" which I think I figured out how to do - I can get a prompt with a #.

Unfortunately the next step - "3. Execute installation program. $ sudo cdroot/autorun" - results in nothing but "command not found". I've tried omitting the $ and I get the same result. If I omit the both the $ and sudo portion  I get "No such file or directory" I can see the directory and file on my hard drive so I know it is there.

I have tried the same steps from the $ prompt but get the same results. I guess I don't know why Smasung tells me to Open "Root Terminal" and then tells me to use the sudu command from a # prompt. Seems these instructions were poorly thought out and not tested by the manufacturer.

Here are the complete instructions:

[Ubuntu OS Installation]

1. Download and extract the driver 

2. Open ''Root Terminal'' 

3. Execute installation program. 

   $ sudo cdroot/autorun

4. After install, PPD path is set again.

   $ sudo ln -s /usr/share/cups/model/samsung /usr/share/ppd/custom/samsung

5. Execute Configurator, and Add your printer model name by Add Printer

Can anyone be so kind as to tell this hapless fool how to interpret these instructions and install my printer? Again, I can't get past step 3.:confused:

---

### Post by quixote on 2010-04-19
Some of the most hopeless instructions I've seen.  They don't even apply to any given linux distribution.  The "open a root terminal" business is more RedHat than Ubuntu, but then they're telling you to "$ sudo etc" which means run a root command in a non-root terminal!  Turkeys.  

(The "$" is the command line prompt.  Sort of like C: on a DOS or Windows machine.  The rest is the bit you type at the prompt, except they've given placeholder terms that you're supposed to fill in with your own paths, but they didn't mention that.  A root prompt is "#".)

Here's what you do.  1) Ignore Samsung.  2) Connect your printer to your ubuntu machine and make sure it's turned on.  3) Go to System > Administration > Printers and click the "New" button toward the top left of the popup window.  It will search for connected printers.  Hopefully, it finds it because figuring out the "URI" is less than simple.

Then (this is from memory) it'll present you with an interminable list of companies and their printers.  Plow through it to find Samsung and then your model. If your model isn't listed you can either try the closest thing to it in the list, or have it look for the driver on your CD from Samsung.  (I believe it also offers to go search the web for you these days.)  If it recommends a driver, accept that because it's usually a safe choice.

After that, I don't remember the steps but I think it's just a matter of clicking "Ok" buttons.  If it asks whether to print a test page, go ahead and try it.

And then come back and let us know whether anything worked! :)

---

### Post by klytu on 2010-04-19
> **LittleFrank said:**
> I'm new to Linux (Ubuntu) and trying to install a printer driver.

I have a Samsung SCX 4826FN for which Samsung provides a Linux "Unified Driver"along with vague instructions for installing it. 

Those instructions tell me to Open "Root Terminal" which I think I figured out how to do - I can get a prompt with a #.

Unfortunately the next step - "3. Execute installation program. $ sudo cdroot/autorun" - results in nothing but "command not found". I've tried omitting the $ and I get the same result. If I omit the both the $ and sudo portion  I get "No such file or directory" I can see the directory and file on my hard drive so I know it is there.

I have tried the same steps from the $ prompt but get the same results. I guess I don't know why Smasung tells me to Open "Root Terminal" and then tells me to use the sudu command from a # prompt. Seems these instructions were poorly thought out and not tested by the manufacturer.

Here are the complete instructions:

[Ubuntu OS Installation]

1. Download and extract the driver 

2. Open ''Root Terminal'' 

3. Execute installation program. 

   $ sudo cdroot/autorun

4. After install, PPD path is set again.

   $ sudo ln -s /usr/share/cups/model/samsung /usr/share/ppd/custom/samsung

5. Execute Configurator, and Add your printer model name by Add Printer

Can anyone be so kind as to tell this hapless fool how to interpret these instructions and install my printer? Again, I can't get past step 3.:confused:

If the method Quixote posted doesn't work, I think I can clarify the confusing instructions you obtained. 

1. First extract the driver you downloaded. To do this, open a terminal window and navigate to wherever you saved the file (I think the name of it is "UnifiedLinuxDriver_1.00.tar.gz"). Then copy and paste this command:
```
tar -xzf UnifiedLinuxDriver_1.00.tar.gz
``` (This creates a directory called "cdroot" which contains another directory called "Linux" and file called "autorun")

2. Then correct way to execute the autorun script is: ```
sudo ./cdroot/autorun
``` (Note: there is a period before "/cdroot/autorun" in that command. Just copying and pasting the commands into the terminal is the easiest way to avoid mistakes - assuming I didn't make any, of course :-))

3. Next do: 
```
sudo ln -s /usr/share/cups/model/samsung /usr/share/ppd/custom/samsung
```

4. After you've completed the above steps you should find an icon on your desktop that's named "Configurator". Double-click it and add your printer model name by Add Printer.

As far as I can tell, that's what you're supposed to do. I tried the above steps from a LiveCD and they seem to be correct. I don't know if the driver works, though, because I don't have your model of printer. Hope this helps and good luck!

---

### Post by quixote on 2010-04-19
Klytu's instructions keep you closer to Samsung's original intent (not to sound like a Supreme Court Justice or anything...) so they may work better for you.  In case it's a useful piece of info: the way you copy and paste into a terminal is use Ctrl-c to copy from this forum (or wherever) and paste into the terminal using **Shift**-Ctrl-v.  In the other direction, select the part you want in the terminal with the mouse, then **Shift**-Ctrl-c to copy.  To paste that elsewhere, it's Ctrl-v, as usual.

---

