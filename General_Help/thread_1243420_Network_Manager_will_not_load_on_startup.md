---
title: "Network Manager will not load on startup"
date: 2009-08-18
forum: General Help
---

### Post by tushar_t on 2009-08-18
Hi,

When I newly installed Ubuntu 9.04 Network Manager was working just fine. It would load on startup and whenever I logged  in Ubuntu, I would be connected automatically to the wireless network. 

But then I was foolishly playing around with NetworkManager earlier to try and get a static IP address. I don't remember which commands I executed in the terminal that could have messed things up. But now what happens is that every time I load Ubuntu, I find that the NetworkManager is not running. So I have to run this command: 

```
sudo NetworkManager
```

before it connects to the network. Under the StartUp applications, the Network Manager option is still checked so I don't know why it wouldn't connect automatically like it used to. Any suggestions?

Thanks.

---

### Post by KlinerDraken on 2009-08-18
Uncheck the Network Manager in StartUp Applications and when you boot up run the command that it runs manualy from the terminal.

nm-applet --sm-disable

And see if you get any errors.

---

### Post by tushar_t on 2009-08-19
Thanks for your reply. I did as you said and executed the  nm-applet --sm-disable command in the terminal.

But nothing happened in the terminal, the cursor went over to the next line and just kept blinking. I didn't get any message and neither did I get to the command prompt. However I did see the Networking icon in the panel in the disconnected mode (as I do when I log in with the Network Manager option in the Startup Applications checked) and NetworkManager still hadn't loaded.

So I pressed Ctrl+C to get back to the command prompt and then this:

```
sudo NetworkManager
nm-applet --sm-disable
```

I was connected to the wireless network then. It seems that NetworkManager just doesn't startup without being manual told to do so in terminal. What should I do?

---

