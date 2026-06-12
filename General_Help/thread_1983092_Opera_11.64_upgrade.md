---
title: "Opera 11.64 upgrade"
date: 2012-05-19
forum: General Help
---

### Post by Silvernail on 2012-05-19
Oneiric
Gnome3

I don't know if this is a problem with Ubuntu, or Opera, or the Ubuntu repository or should I even be concerned.

Because Firefox became so unstable I have started using Opera. Over the past couple months at least once a day I get notice to upgrade to Opera 11.64.

I did. I allowed the Ubuntu software center to install it for me. Which it tells me it did. I got to the software center, search for Opera and it pops up as version 11.64 and tells me it is installed. Asking me to reinstall. Sometimes I do.

I load Opera > Help > About and it says version 11.11. I am still getting upgrade notices.

Can someone advise me what to do?
Thanks
Dave

---

### Post by zvacet on 2012-05-20
Try from terminal

```
sudo apt-get update && sudo apt-get upgrade
```

and see if you get any errors.If you do paste them here ( from starting command to the end )

If you have synaptic try to update with it.Click on refresh and after that on mark all updates.If you don´t have synaptic install it

```
sudo apt-get install synaptic
```

If previous two doesn´t work download Opera from [here.]("http://www.opera.com/browser/download/")Install it from terminal

```
sudo dpkg -i <packagename>
```

---

### Post by Silvernail on 2012-05-20
Synaptic tells me that version 11.64 1403 is installed. As does the software center.

Guess I'll just put with  the notice popping up and not worry about it.

Thanks for the feedback and thoughts.

Dave

---

### Post by zvacet on 2012-05-20
You can try to reinstall Opera from synaptic and see if that make any changes.

---

### Post by Silvernail on 2012-05-20
Might try that, thanks for the suggestion.

---

