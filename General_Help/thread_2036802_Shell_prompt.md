---
title: "Shell prompt"
date: 2012-08-02
forum: General Help
---

### Post by D3L373 on 2012-08-02
Hey experts. I created a shell script, whenever I attempt to launch it I receive a popup window:

> Do you want to run "name.sh", or display its contents?
"name.sh" is an executable text file.

Run in Terminal | Display | Cancel | RunI would like to know if there is a way to have this just run without a prompt.

I've checked through the forum, also google searching, and came up blank. There's nothing in the properties of the file (from what I can see) that allows it to auto-run.

---

### Post by Dylan1473 on 2012-08-02
You can either run it from the terminal manually every time (which I'm guessing you don't want to do) or just make a shortcut and point it to the script, then use the shortcut to run it. The shortcut will automatically run it as a script.

EDIT: Oh, and I'm not 100% certain, but I don't think this actually occurs in all variants. I seem to recall using at least one desktop environment/window manager where it didn't happen (again, not 100% sure, and couldn't even name which), and I know in my current one (Enlightenment) the box actually gives the options Execute, Execute in Terminal, and Cancel.

---

### Post by OM55 on 2012-08-02
Hello D3L373,

There is a very simple way to do just that by changing the setting in Nautilus:

1. Open your nautilus (you can even just type 'nautilus' at a terminal)
2. In the menu: Edit -> Preferences
3. Select the 'Behaviour' tab
4. Change the selection of 'Executable Text Files' from 'Ask Each Time' to 'Run Executable Text'

Now, in order to be able to run a shall script as such, you should remember to change its permissions to include the 'Run' permission. 
You can do that by selecting it and right-mouse-click, then 'Properties', select the 'Permissions' tab, and check the 'Allow executing file as a program' box.

That's it.

Hope that helps!

---

### Post by D3L373 on 2012-08-02
> **OM55 said:**
> Hello D3L373,

There is a very simple way to do just that by changing the setting in Nautilus:

1. Open your nautilus (you can even just type 'nautilus' at a terminal)
2. In the menu: Edit -> Preferences
3. Select the 'Behaviour' tab
4. Change the selection of 'Executable Text Files' from 'Ask Each Time' to 'Run Executable Text'

Now, in order to be able to run a shall script as such, you should remember to change its permissions to include the 'Run' permission. 
You can do that by selecting it and right-mouse-click, then 'Properties', select the 'Permissions' tab, and check the 'Allow executing file as a program' box.

That's it.

Hope that helps!

Great, thank you very much! It's resolved. \\:D/

---

### Post by OM55 on 2012-08-02
You are very welcome.

(Please remember to change this thread to 'Solved')

---

