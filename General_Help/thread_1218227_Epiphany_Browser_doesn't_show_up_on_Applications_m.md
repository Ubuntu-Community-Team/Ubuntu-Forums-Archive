---
title: "Epiphany Browser doesn't show up on Applications menu"
date: 2009-07-20
forum: General Help
---

### Post by Nazaroo on 2009-07-20
I installed Epiphany using the Add/Remove (it doesn't show up as an option in the Synaptic Package Manager).

It did not however show up under 'internet' in the dropdown menus.

So I also tried 

```
 sudo apt-get install epiphany-browser epiphany-extensions
 


```
This added the extensions too, but still Epiphany doesn't show up in the pulldown menus.


any ideas?

Nazaroo

---

### Post by ellgor on 2009-07-20
Hi,

A suggestion, search for Firefox in synaptic, for some reason epiphany is located above it here and not as an individual package (something to do with being Gecko based or something or other) hope this helps.

Regards, Ellgor. (using Epiphany right now).

---

### Post by Simian Man on 2009-07-20
If the program is really installed (you can test if it by launching it from the terminal), you can add a menu item yourself:
[LIST=1]
[*]Right click on the menu and choose "edit menus"
[*]Under the internet tab, click "new item"
[*]Put Epiphany for the name, "epiphany" for the command and whatever you want for the comment
[*]If you want you can make an icon for it
[/LIST]

BTW Father Dougal is hilarious!

---

### Post by Nazaroo on 2009-07-21
> **Simian Man said:**
> If the program is really installed (you can test if it by launching it from the terminal), you can add a menu item yourself:
[LIST=1]
[*]Right click on the menu and choose "edit menus"
[*]Under the internet tab, click "new item"
[*]Put Epiphany for the name, "epiphany" for the command and whatever you want for the comment
[*]If you want you can make an icon for it
[/LIST]

BTW Father Dougal is hilarious!

Thanks!  I was wondering how to edit the pulldowns...

The Father Ted series was one of the best recent British comedy shows in a while!

And Dougle is a brilliant character!  

[http://www.youtube.com/watch?v=4uOX_hbkAMc](http://www.youtube.com/watch?v=4uOX_hbkAMc)

Here's a link to the 'booby trap' episode...lol

---

### Post by Nazaroo on 2009-07-21
> **ellgor said:**
> Hi,

A suggestion, search for Firefox in synaptic, for some reason epiphany is located above it here and not as an individual package (something to do with being Gecko based or something or other) hope this helps.

Regards, Ellgor. (using Epiphany right now).

I shut down and rebooted...and Epiphany showed up in the menus..

Who knew? 

They could add a line to the documentation...

---

### Post by Simian Man on 2009-07-21
> **Nazaroo said:**
> The Father Ted series was one of the best recent British comedy shows in a while!

And Dougle is a brilliant character!  

[http://www.youtube.com/watch?v=4uOX_hbkAMc](http://www.youtube.com/watch?v=4uOX_hbkAMc)

Here's a link to the 'booby trap' episode...lol

Ha that's hilarious.  I also love the [Spider Baby episode]("http://www.youtube.com/watch?v=5AB7IDw3PNI") :).

---

