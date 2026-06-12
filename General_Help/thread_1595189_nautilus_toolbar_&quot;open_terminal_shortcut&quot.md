---
title: "nautilus toolbar &quot;open terminal shortcut&quot;"
date: 2010-10-13
forum: General Help
---

### Post by krishna1650 on 2010-10-13
Hello all, 
I want to know, how to make a shortcut of "open terminal" in the nautilus toolbar. I have installed "nautilus open terminal", there is option for opening terminal in right click menu and file tab in menu bar. But i want the shortcut to be in toolbar. I tried to edit "/usr/share/nautilus/ui/nautilus-navigation-window-ui.xml" file, but i don't know the action name, i could not add that shortcut.

Thanks and regards

---

### Post by arkadios on 2010-10-13
This might be what you're looking for: [http://priyank.co.in/command-prompt-here-in-nautilus-gnome](http://priyank.co.in/command-prompt-here-in-nautilus-gnome)

---

### Post by krishna1650 on 2010-10-13
> **arkadios said:**
> This might be what you're looking for: [http://priyank.co.in/command-prompt-here-in-nautilus-gnome](http://priyank.co.in/command-prompt-here-in-nautilus-gnome)

Thanks for the reply. But i already have this setup, i can open terminal from right click. What i want terminal shortcut in the toolbar.

Thanks again for reply.

---

### Post by arkadios on 2010-10-13
Sorry, I forgot to also add, when you're adding the action, don't forget to click "Display item in the toolbar." It's right under the context label.

---

### Post by krishna1650 on 2010-10-13
> **arkadios said:**
> Sorry, I forgot to also add, when you're adding the action, don't forget to click "Display item in the toolbar." It's right under the context label.

Thanks,
Actually i also tried that, but terminal opens with parent directory not current directory as working directory.

Hope, i made the point clear, and i am going to try again (hope, first time, i made a mistake)

Thanks

---

### Post by arkadios on 2010-10-13
All I can say is that I had to make sure to put *--working-directory=%d/%f* in the parameters and leave *gnome-terminal* in the path alone or else it wouldn't work.

Hope all goes well.

---

### Post by krishna1650 on 2010-10-13
> **arkadios said:**
> All I can say is that I had to make sure to put *--working-directory=%d/%f* in the parameters and leave *gnome-terminal* in the path alone or else it wouldn't work.

Hope all goes well.

thanks, it's working perfectly.

---

### Post by adf88 on 2011-09-26
To handle spaces in directory names set command ...

... path to```
sh
```... and parameters to```
-c "echo '%f' | sed 's/%%20/ /g' | xargs -I {} gnome-terminal --working-directory='{}'"
```

Probably it can be done better, but it works.

---

### Post by rober60 on 2011-09-26
I poverty to pair, how to puddle a route of "arise tangency" in the argonaut toolbar. I **** installed "pigboat open terminus", there is option for opening contact in sect depression listing and record tab in schedule bar. But i impoverishment the crosscut to be in toolbar.





  [Mercury   Power Steering Gear Box](http://www.carsteering.com/steeringparts/Mercury/Power_Steering_Gear_Box.html)

---

