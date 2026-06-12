---
title: "Very frustrating problem"
date: 2011-04-29
forum: General Help
---

### Post by haqzor7 on 2011-04-29
Hi everyone, I'm as you may guess new to ubuntu, I have had it for about a month now and randomly my Openoffice just CRASHED! I tried google, and searched the forums, I found delete some hidden file (/home/(user)/.openoffice2) and that just stopped openoffice from loading at all! please help :(

                     ~haqzor7

---

### Post by dylbud on 2011-04-29
I would try first going into the Ubuntu Software Center from the main menu, find openoffice and uninstall all the openoffice programs, then reinstall. That's the first thing I would try.

---

### Post by haqzor7 on 2011-04-29
Kk, Ill try that and post asap, THIS IS GETTING SO ANNOYING

---

### Post by haqzor7 on 2011-04-29
> **dylbud said:**
> I would try first going into the Ubuntu Software Center from the main menu, find openoffice and uninstall all the openoffice programs, then reinstall. That's the first thing I would try.
Is there a way to uninstall and reinstall all at once?

---

### Post by dylbud on 2011-04-29
I don't think there is, but I might be wrong. Seems like doing both at the same time would cause conflicts in trying to write/remove files. That's just my gut feeling.

Is is it taking a long time to uninstall? Hopefully this works. If not, the next step I personally would try would be to download the source file from OpenOffice dot org and install from source. That can also be intimidating for a noob but it's not that hard really. See [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) for instructions.

---

### Post by haqzor7 on 2011-04-30
> **dylbud said:**
> I would try first going into the Ubuntu Software Center from the main menu, find openoffice and uninstall all the openoffice programs, then reinstall. That's the first thing I would try.
Ok, I uninstalled all, and I only installed what I needed, (Openoffice Database) And still it wont load :/ Compiling from source, Iv heard of that, would it really work?
[EDIT] Is there a way to sudo it? (IE in win you could run things as administrators) Or does ubuntu not do that?
                      ~haqzor7 ](*,)

---

### Post by dylbud on 2011-04-30
I don't know for sure if compiling from source would work, but it has worked for me in the past when I was having trouble with installations of programs. (never open office tho).

The software center is just a nice GUI with a bunch of popular programs, but all those programs are also in the Synaptic Package Manager (main menu --> Administation), which is still a GUI, but a bit more advanced. There you can pick all the packages by that same name that you would use if you used sudo apt-get. In a sense, Synaptic Package Manager is just a GUI version of apt-get.

So the point is, you could try sudo apt-get, but I think it's just installing the same package as the Software Center just did. I may be wrong, as you have to enter a password for Synaptic or apt-get, giving you higher admin privileges -- maybe worth trying.

Another thing you could try is LibreOffice. Its the new thing. LibreOffice is the same program as openOffice, it's just been renamed and being redistributed due some disputes between Oracle, Sun Microsystems, blah blah... But it might work because although its the same program, it's a different brand and a different organization providing it -- it probably gets installed in its own set of folders.

Newer versions of ubuntu are coming packaged with LibreOffice, I heard. Maybe you already have it?

---

### Post by haqzor7 on 2011-04-30
Nope, Ill check it out,

---

### Post by haqzor7 on 2011-04-30
> **dylbud said:**
> I don't know for sure if compiling from source would work, but it has worked for me in the past when I was having trouble with installations of programs. (never open office tho).

The software center is just a nice GUI with a bunch of popular programs, but all those programs are also in the Synaptic Package Manager (main menu --> Administation), which is still a GUI, but a bit more advanced. There you can pick all the packages by that same name that you would use if you used sudo apt-get. In a sense, Synaptic Package Manager is just a GUI version of apt-get.

So the point is, you could try sudo apt-get, but I think it's just installing the same package as the Software Center just did. I may be wrong, as you have to enter a password for Synaptic or apt-get, giving you higher admin privileges -- maybe worth trying.

Another thing you could try is LibreOffice. Its the new thing. LibreOffice is the same program as openOffice, it's just been renamed and being redistributed due some disputes between Oracle, Sun Microsystems, blah blah... But it might work because although its the same program, it's a different brand and a different organization providing it -- it probably gets installed in its own set of folders.

Newer versions of ubuntu are coming packaged with LibreOffice, I heard. Maybe you already have it?
How would I get it? I tried "sudo apt-get LibreOffice" Nothing, and I cant get it in Software center :(

---

### Post by littlebull38 on 2011-04-30
I have never had an issue with Open Office, I use it all day everyday.
 I let my desktop upgrade to this 11.10 or what ever, Not Open Office any more, looks the same, new name.
I think it runs slower, but it works, I guess you could upgrade,,,,?????

---

