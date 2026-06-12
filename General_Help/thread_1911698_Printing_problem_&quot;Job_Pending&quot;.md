---
title: "Printing problem &quot;Job Pending&quot;"
date: 2012-01-19
forum: General Help
---

### Post by oxf on 2012-01-19
Hi,

I am at my wits end with this printing problem. 
The printer is a basic Epson Stylus S22 and all I want to do for now is print a basic black/white document.

This all started a week ago, before that it printed fine. 

Then it refused to print and in the Print Queue I would get the message "job pending" or ocasionally "processing"  

It seemed as I might be low on the color ink since they were just the "starter cartridges.  Although I was only printing black/white I replaces all cartridges in case the colour was stopping all printing.

It still refuses to print  and I have reinstalled the drivers without success. So it seems somehow the PC is not sending the print job to the printer maybe?

I know "job pending" is not much information to go on but can anyone sugest a solution or a diagnostic procedure to get to the bottom of this?

Thanks
Katya

---

### Post by plucky on 2012-01-19
> **oxf said:**
> Hi,

I am at my wits end with this printing problem. 
The printer is a basic Epson Stylus S22 and all I want to do for now is print a basic black/white document.

This all started a week ago, before that it printed fine. 

Then it refused to print and in the Print Queue I would get the message "job pending" or ocasionally "processing"  

It seemed as I might be low on the color ink since they were just the "starter cartridges.  Although I was only printing black/white I replaces all cartridges in case the colour was stopping all printing.

It still refuses to print  and I have reinstalled the drivers without success. So it seems somehow the PC is not sending the print job to the printer maybe?

I know "job pending" is not much information to go on but can anyone sugest a solution or a diagnostic procedure to get to the bottom of this?

Thanks
Katya


Try opening the CUPS interface and see if there are any messages or logs.

From Firefox put in the address bar ```
http://127.0.0.1:631/
```

Good Luck

---

### Post by Scott Baker on 2012-01-19
Hi Katya. It's going to sound strange, but I've had to do this, and it's corrected the problem every time I've done it. First, uninstall your printer from your machine, and unplug its cable from the back of your machine. Now reboot your machine, and check to see that you have no printer on this machine. Now shut your machine down, plug the printer back in (but don't turn it on yet). Now, reboot your machine and make sure you're online. Turn your printer back on, and it should start loading back onto your machine, good as new. (Before anyone asks about being online, I've had 2 Kodak printers that wouldn't load correctly without being online, must have been drivers). This may sound time consuming, but it shouldn't take more than about 10 minutes. [-o<

---

### Post by oxf on 2012-01-19
> **plucky said:**
> Try opening the CUPS interface and see if there are any messages or logs.

From Firefox put in the address bar ```
http://127.0.0.1:631/
```Good Luck

> **Scott Baker said:**
> Hi Katya. It's going to sound strange, but I've had to do this, and it's corrected the problem every time I've done it. First, uninstall your printer from your machine, and unplug its cable from the back of your machine. Now reboot your machine, and check to see that you have no printer on this machine. Now shut your machine down, plug the printer back in (but don't turn it on yet). Now, reboot your machine and make sure you're online. Turn your printer back on, and it should start loading back onto your machine, good as new. (Before anyone asks about being online, I've had 2 Kodak printers that wouldn't load correctly without being online, must have been drivers). This may sound time consuming, but it shouldn't take more than about 10 minutes. [-o<

Well thanks but unfortunately that didn't work and I tried it several times! BTW The PC didn't detect the printer autonatically and I had  to use "Add Printer"

@plucky
The only error I'm getting in CUPS is:

  
```
E [19/Jan/2012:13:18:08 +0000] [CGI] Unable to scan "@LOCAL"!

```
Katya

---

### Post by oxf on 2012-01-19
Well I tried connecting the printer to a friends laptop and it printed OK.
So at least we know the printer works. What is it about my PC thats a problem :confused:

---

### Post by oxf on 2012-01-20
Does any one have any sugestions how to diagnose this problem? 
As of right now I'm dead in the water.
I can print from a friends Laptop (using Ubuntu also) but not from my PC

Please help someone :)

Thanks
Katya

---

### Post by plucky on 2012-01-21
> **oxf said:**
> Does any one have any sugestions how to diagnose this problem? 
As of right now I'm dead in the water.
I can print from a friends Laptop (using Ubuntu also) but not from my PC

Please help someone :)

Thanks
Katya

Try **System > Administration > Printing > Help > Troubleshooting** or in 11.10 **System Settings > Printing > Help > Troubleshooting** and see what it says.

Good Luck

---

### Post by Scott Baker on 2012-01-24
Hi again Katya. Lets try something else here. Go to your synaptic package manager and open that up. In the quick filter near the top of that screen, put in the word CUPS. (common UNIX printing system). Under that, you should see several items that have a green box (as opposed to clear), and Ubuntu logos next to them. Follow that list down, and ALL of the boxes that are green, click those, then click "mark for reinstallation'. When you're done marking all of the green marked boxes, go up to the word "apply" and click that. That action will reload your print software. Take a few more minutes to uninstall then reinstall your printer per previous posting. Try that, and see if that FINALLY gets you going again. Good luck, ScottyB  [-o<

---

### Post by oxf on 2012-02-12
> **Scott Baker said:**
> Hi again Katya. Lets try something else here. Go to your synaptic package manager and open that up. In the quick filter near the top of that screen, put in the word CUPS. (common UNIX printing system). Under that, you should see several items that have a green box (as opposed to clear), and Ubuntu logos next to them. Follow that list down, and ALL of the boxes that are green, click those, then click "mark for reinstallation'. When you're done marking all of the green marked boxes, go up to the word "apply" and click that. That action will reload your print software. Take a few more minutes to uninstall then reinstall your printer per previous posting. Try that, and see if that FINALLY gets you going again. Good luck, ScottyB  [-o<

Thanks Scotty for that and I will try that. I'm not at home in the UK but on the  W coast of the US right now. But no the printer problem was never resolved before I left ( I had to resort to printing my tickets at the public library!) So when I return in a couple of weeks I will be returning to the non functioning printer again and will need to pick up the problem and resolve it. When I get back I will try what you suggest and post result.

Thanks again
Katya

---

