---
title: "Mozilla Thunderbird"
date: 2011-06-05
forum: General Help
---

### Post by BSG Fan on 2011-06-05
Hey guys
I just downloaded the Mozilla Thunderbird from its website 
The question is:
where in "Applications" is it?
Was not supposed to be at "Applications" - "Internet"?

Where is the Thunderbird?

ps:
When I tried to download it originally from the "Ubuntu Software Center" or the "System-Administration- Synaptic Package Manager" they told me that the packages were from untrusted sources, etc.... But I downloaded from its website... ????

How can I un-install the Thunderbird if it doesn't help me?

---

### Post by howefield on 2011-06-05
Have you installed it ?

---

### Post by Rebelli0us on 2011-06-05
you don't have to download anything, just type "thunderbird" in Ubuntu software center and select "install"

---

### Post by BSG Fan on 2011-06-05
> **howefield said:**
> Have you installed it ?

Yes, I installed it from [http://www.mozillamessaging.com/en-US/thunderbird/](http://www.mozillamessaging.com/en-US/thunderbird/)

But I can not find it anywhere, except of course the package where I downloaded.

---

### Post by BSG Fan on 2011-06-05
I am confused guys
I indeed downloaded and later extracted it.
If it is not installed what can I do?

Any code for the terminal?
Do I have to remove it and install again?
How I will remove it?

:confused:

---

### Post by howefield on 2011-06-05
Your screenshots are only shots showing you downloaded the package, doesn't mean you installed it.

Try opening a terminal and type

> thunderbird

and press enter. Does the application open ?

As mentioned above, there is no reason not to install via Ubuntu Software Centre.

---

### Post by BSG Fan on 2011-06-05
> **howefield said:**
> Your screenshots are only shots showing you downloaded the package, doesn't mean you installed it.

Try opening a terminal and type



and press enter. Does the application open ?

As mentioned above, there is no reason not to install via Ubuntu Software Centre.
Hi Howefield and Rebelli0us
Ok, I went back to the Ubuntu Software Center, and look what happened when I tried to download it from there: please see the new 2 attachments

So, the Ubuntu Software Center does not allow me to download/instyll it.

---

### Post by SeijiSensei on 2011-06-05
I don't know why it's telling you the package is untrusted unless you're trying to install it from a third-party repository (like a "PPA") for which you didn't get the key.

If you did add a PPA for Thunderbird, remove it, and try running apt-get again so you get the one from the standard repositories.

In general, you rarely if ever need to install software from any place other than the repositories.

---

