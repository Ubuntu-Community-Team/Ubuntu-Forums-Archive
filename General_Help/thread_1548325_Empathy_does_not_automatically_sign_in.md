---
title: "Empathy does not automatically sign in"
date: 2010-08-08
forum: General Help
---

### Post by fterh on 2010-08-08
Hello, everytime I log in, I get a prompt asking me to enter my password to unlock the keyring. Then when I open Empathy, I am not automatically connected. When I open my empathy accounts (F4), it says Available but I am not signed in. I have to remove and re-add my account.

Is this normal? :(

---

### Post by chopinhauer on 2010-08-08
> **fterh said:**
> Hello, everytime I log in, I get a prompt asking me to enter my password to unlock the keyring. Then when I open Empathy, I am not automatically connected. When I open my empathy accounts (F4), it says Available but I am not signed in. I have to remove and re-add my account.


In Empathy Accounts you can activate and deactivate your accounts, otherwise there is an option in the Preferences whether or not to log into the accounts at (Empathy) startup.

---

### Post by fragos on 2010-08-08
This is a pain. It seems that once a chat accounts connection is broken, it stays that way. Getting Chats started is a 3 step process. 1st you have to open the Accounts preferences and disable and re-enable each account. They should connect. Next open the System Monitor - Processes tab - select empathy - end process button. 3rd, restart empathy. The chat icon will appear in the applet bar and you're up and running. You can accomplish the same steps at the CLI.

---

### Post by gauravbutola on 2010-08-08
> **fragos said:**
> This is a pain. It seems that once a chat accounts connection is broken, it stays that way. Getting Chats started is a 3 step process. 1st you have to open the Accounts preferences and disable and re-enable each account. They should connect. Next open the System Monitor - Processes tab - select empathy - end process button. 3rd, restart empathy. The chat icon will appear in the applet bar and you're up and running. You can accomplish the same steps at the CLI.

I dont know what goes wrong with you but my empathy runs quite fine (with some minor flaws). At startup It does not make me signed in automatically (though I checked mark to make it startup sign in) but I have to open empathy and just set it to available and thats it, I am online in all my chat accounts.
One other minor problem for me is I checked to make it sound when someone comes online and offline but it never does that. But sure i Can live my life without that ;)

---

### Post by fragos on 2010-08-08
> **gauravbutola said:**
> I dont know what goes wrong with you but my empathy runs quite fine (with some minor flaws). At startup It does not make me signed in automatically (though I checked mark to make it startup sign in) but I have to open empathy and just set it to available and thats it, I am online in all my chat accounts.
One other minor problem for me is I checked to make it sound when someone comes online and offline but it never does that. But sure i Can live my life without that ;)

Did some more experimentation and found I don't need to toggle each account, only end the empathy process and start it again.

---

### Post by fterh on 2010-08-08
I decided to use Pidgin instead.

---

### Post by ashjas on 2010-10-19
> **fterh said:**
> I decided to use Pidgin instead.

ya and pidgin has a bloody bug that when i sign in to gtalk using it.. it removes my gmail chat/profile image because by default pidgin doesnot use the current google profile picture and sets its own blank image!

---

### Post by fiercemoose on 2010-10-24
Why is this marked as SOLVED? It isn't solved. I have the same problem and I don't see any sort of resolution here...

---

### Post by howefield on 2010-10-24
The OP has decided that the thread has been solved to his/her satisfaction after taking the option to use an alternative application. 

If you need help support, feel free to start a thread.

---

### Post by freeazy on 2010-10-24
> **fterh said:**
> Hello, everytime I log in, I get a prompt asking me to enter my password to unlock the keyring. Then when I open Empathy, I am not automatically connected. When I open my empathy accounts (F4), it says Available but I am not signed in. I have to remove and re-add my account.

Is this normal? :(

This problem happens to me everytime I connect via wvdial, but if i connected through the Network Manager, Empathy will signed automatically and you don't need re-add account.

---

