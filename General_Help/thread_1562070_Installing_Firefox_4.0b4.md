---
title: "Installing Firefox 4.0b4"
date: 2010-08-27
forum: General Help
---

### Post by fterh on 2010-08-27
I downloaded the .tar.bz2 and extracted it. I can run Firefox 4.0b4 fine by running the firefox executable, but I get an annoying popup asking if I want to run it in terminal, etc. Also I cannot run "firefox -profilemanager" in Terminal to get it to use my existing profile from Windows 7.

Hmm. How do you install Firefox completely such that the command firefox is recognized?

---

### Post by ptptaylor on 2010-08-27
Take a quick look over at this link:

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

It 'should' walk you through the latest installation I'm guessing!

Yeah just take a look at the daily updates section ;)

---

### Post by mikewhatever on 2010-08-27
./firefox -P

...and select the profile you want. Is there a reason why you can't do that?

---

### Post by fterh on 2010-08-27
Okay thanks guys got it. Just out of curiosity, is it possible for me to create a "firefox" command that would run Firefox 4.0b4?

---

### Post by mikewhatever on 2010-08-27
fterh, not sure what you mean by creating a command. The command I posted above will run it, and there also seems no reason why you couldn't put it into a launcher.

---

### Post by fterh on 2010-08-27
I mean like creating a command such that running "firefox" in Terminal will launch it, rather than "./firefox".

---

### Post by mikewhatever on 2010-08-27
Sure, you just need to link 'firefox' to the firefox4 executable.

1.Rename the existing firefox executable:
sudo mv /usr/bin/firefox /usr/bin/firefox-old

2.Create a new link:
sudo ln -s /full-path-to-firefox4-executable /usr/bin/firefox

The full path depends on where you've saved Firefox 4. Let's assume it's in your home folder, and your username is fterh. The command will look as follows:
sudo ln -s /home/fterh/firefox/firefox /usr/bin/firefox

---

### Post by fterh on 2010-08-27
But this involves mapping an existing command to a new target right?

I have uninstalled my old Firefox, so now "firefox" command is unmapped to any executable.

---

### Post by mikewhatever on 2010-08-27
> **fterh said:**
> But this involves mapping an existing command to a new target right?
Something like that.

> I have uninstalled my old Firefox, so now "firefox" command is unmapped to any executable.
The second command above will place a link to the FF4 executable into /usr/bin, so that the system knows what to do with the 'firefox' command.

---

