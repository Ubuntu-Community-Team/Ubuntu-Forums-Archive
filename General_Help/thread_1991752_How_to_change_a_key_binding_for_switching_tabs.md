---
title: "How to change a key binding for switching tabs"
date: 2012-05-30
forum: General Help
---

### Post by naoyamakino on 2012-05-30
Hi there, I would like to change a global keybinding of Switch to next tab to be <Fn>Tab and Switch to Previous Tab to be <Fn><Shift>Tab, but I can't seem to accomplish that.

Is there anyway I can change a global keybinding to do that?

Here is my version:

> naoyamakino@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise

thank you for your kind help, any feedback would be very much appreciated.
cheers

---

### Post by zombifier25 on 2012-05-30
The Fn key is hardwired into the laptop. When you press the Fn key, it sends a signal to the hardware itself, not the OS, unlike the Ctrl, Shift,... keys. So theoretically it's impossible.
You can read more on the Fn key here: [https://en.wikipedia.org/wiki/Fn_key](https://en.wikipedia.org/wiki/Fn_key)

---

### Post by naoyamakino on 2012-05-31
hi zombifier25, thanks for your reply. Ok then, what about <Alt>Tab and <Alt><Shift>Tab? I would like to know where/how I can customize global key bindings for switching tabs.

any thoughts?
thanks for your reply.

---

### Post by zombifier25 on 2012-05-31
(I'm not aware of any more user friendly way than this)
Install ccsm:
```
sudo apt-get install compizconfig-settings-manager
```
Then open ccsm. Be careful in it, you have been warned by the dialog. Choose Unity Plugin, and you should see the option to change the keybindings for app switching in there.

---

### Post by naoyamakino on 2012-05-31
Hi zombifier25, thanks again for your reply. I do have ccsm and played around with it. but there is no options to switch tabs in Ubuntu Utility Plugins. those listed there are only for application switchers and flip through windows as you mentioned.
But what I am looking for is keybinding for switching tabs within a window. Like going to a next tab in chrome.

Do you have any ideas how to change that configurations?
thank you so much for your help.

regards
Naoya

---

### Post by matt_symes on 2012-06-01
Hi

> I would like to change a global keybinding of Switch to next tab

In response to your PM...

I'm not quite with you when you say "tab". Is this switching tabs in an application such as Firefox ? Switching windows ? switching workspaces ?

Can you give your current key bindings so i can see myself and can you explain what you mean by "tab" in more detail please.

Kind regards

---

### Post by naoyamakino on 2012-06-07
Hi matt_symes, thanks for your reply. I mean, a tab in an application, like chrome tabs and terminal tabs in one window. I would like to change a keybinding so that I can go to next tab by <Alt>Tab and previous tab by <Alt><Shift>Tab.

current keybindings are following:
switch_to_workspace_down: <Control>Down
switch_to_workspace_up: <Control>Up
switch_to_workspace_right: <Control>Right
switch_to_workspace_left: <Control>Left

and here is the current setting of Ubuntu Utility Plugin
[http://ow.ly/i/Gj3j/original](http://ow.ly/i/Gj3j/original)

I appreciate your feedback.
regards

---

### Post by matt_symes on 2012-06-09
Hi

@naoyamakino

I have to be honest. I'm not sure how to do that. I suspect someone else will have an idea though.

Kind regards

---

