---
title: "Update Manager and Synaptic Package Manager Fault"
date: 2011-12-08
forum: General Help
---

### Post by dannybate on 2011-12-08
Hi there, 

I am having issues with my version of 10.10

I am receiving error messages from the Update Manager and the Syna[tic Package Manager.

Here is the error i am receiving:-

[IMG]http://i.imgur.com/UYb7Q.png[/IMG]

[IMG]http://i.imgur.com/PA8Ke.png[/IMG]

Any advice and help will be greatly appreciated.

---

### Post by BC59 on 2011-12-08
Try this:

In a terminal ```
sudo gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
```

Then switch software sources from your country to main, or search for best server

Finally run:
```
sudo apt-get install -f
```

---

### Post by Frogs Hair on 2011-12-08
I have seen this before and simply running the update manager solved the problem . Running the commands will preform the same task ```
sudo apt-get update
``` ```
sudo apt-get upgrade
```

---

### Post by dannybate on 2011-12-08
> **BC59 said:**
> Try this:

In a terminal ```
sudo gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
```Then switch software sources from your country to main, or search for best server

Finally run:
```
sudo apt-get install -f
```


brilliant stuff, worked like a charm

---

### Post by BC59 on 2011-12-08
Then mark the thread as solved to help other people with the same problem. You can mark it through Thread Tools close to the top of the page.

---

