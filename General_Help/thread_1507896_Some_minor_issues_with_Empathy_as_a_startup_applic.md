---
title: "Some minor issues with Empathy as a startup application."
date: 2010-06-12
forum: General Help
---

### Post by Kep on 2010-06-12
So, here's the thing.

It used to be that I had an empathy quick launch in AWN, which ran the command "empathy" when I clicked on it. What this would do was change my status from "offline" to "online"; it wouldn't show the contact list or open any other windows. This seems to be the default behaviour.

Well that's fine, but I figured that it would be useful to have this as something which happens whenever I boot up Ubuntu. So I added empathy to the "startup applications" list, again with the command "empathy".

What happens now, is that when I boot up, nothing happens. I don't go online and the contact list doesn't appear. When I click the empathy icon, my contact list appears, but I don't come online. Odd.

Also, my contact list has stopped showing my contacts...

In gconf-editor, "main_window_hidden" is set to true.

Oh and in empathy preferences&#8212;general&#8212;auto connect on startup is set to true as well

Now what I *want* to happen is that when I boot up, I am automagically online, and clicking on the icon opens the contact list.

Help?

I'm running Ubuntu Lucid Lynx and Empathy 2.30.1

---

### Post by JouniL on 2011-08-02
I had the same problem, but with Ubuntu 11.04 Natty Narwhal.

I added Empahty to the startup applications with command "empathy -h" then it started to work properly.

Hope this helps you!

---

