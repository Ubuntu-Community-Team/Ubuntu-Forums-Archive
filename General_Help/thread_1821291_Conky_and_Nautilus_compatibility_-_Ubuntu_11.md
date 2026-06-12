---
title: "Conky and Nautilus compatibility - Ubuntu 11"
date: 2011-08-08
forum: General Help
---

### Post by victoroliveira on 2011-08-08
So guys, here i bring a little bit of my Conky-colors code, i was having some problems to configure it and here's the thing.. for those who use nautilus configuration and are having problem with the configuration of the Own_type set i suggest do type desktop, normal or override.

Here, to set desktop i got a kind of lag in my desktop area, and realy didnt worked. so, i tried to put the normal Own_type, but was still having some problems, the conky dissapear a few seconds later but it's still runnning in the process. There are two ways to solve this problem.

#############################
# - Window specifications - #
#############################
own_window_class Conky
own_window yes
own_window_type normal
own_window_transparent yes
**own_window_argb_value 255**
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

set that command line on your configuration and you will have the conky working normaly. The other way to solve the problem is to put  "own_window_transparent no" but this method is realy ugly to the interface. I hope i could help someone with these 'cause i spend hours and hours looking for how to solve this problem in the internet and nobody posted something like this!

---

