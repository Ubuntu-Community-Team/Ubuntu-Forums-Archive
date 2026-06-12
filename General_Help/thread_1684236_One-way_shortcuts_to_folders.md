---
title: "One-way shortcuts to folders?"
date: 2011-02-08
forum: General Help
---

### Post by viktorzk on 2011-02-08
Hello,
Suppose that I create a shortcut to the folder /abc/def and place the shortcut in /xyz. Opening the shortcut leads to /xyz/def. Is it possible the shortcut to lead to /abc/def instead?
Edit: I use nautilus, not the shell.
I know how to create a script to do that, but I would rather keep things simple.
Thanks!

---

### Post by Smart Viking on 2011-02-08
It may appear that it's creating a new directory, and if you print pwd it will print /xyz/def, but you're actually in /abc/def. Creat a file in /xyz/def/ and go to /abc/def, and it will be there. So the best answer I have for you by making it "look like" you're there, is to cd into the location where symlink leads.
Btw how would you know how to create a script to do it, but not be able to do it? O.o

```
ln -s /abc/def /xyz/def
```

---

### Post by viktorzk on 2011-02-08
I should have mentioned that I mostly live in the GUI (sorry to disappoint!).
When I open the shortcut in nautilus, its location field shows /xyz/def, so I don't have the option to jump to /abc by going up one folder. I guess this also answers your question :)

---

### Post by tgm4883 on 2011-02-08
> **viktorzk said:**
> I should have mentioned that I mostly live in the GUI (sorry to disappoint!).
When I open the shortcut in nautilus, its location field shows /xyz/def, so I don't have the option to jump to /abc by going up one folder. I guess this also answers your question :)

Don't go up, go back. You are creating a shortcut to another location, so when you click on that shortcut, you are transported to that location.

---

### Post by viktorzk on 2011-02-08
> **tgm4883 said:**
> Don't go up, go back. You are creating a shortcut to another location, so when you click on that shortcut, you are transported to that location.
 
The 'back' button is greyed out in nautilus.

---

### Post by tgm4883 on 2011-02-09
> **viktorzk said:**
> The 'back' button is greyed out in nautilus.

If the back button is greyed out, it sounds like you have other issues. The back button should not be greyed out after changing directories

---

### Post by wujj123456 on 2011-02-09
The only thing I can think of is to create a new file
put in: 
nautilus <target directory>

For your example, create a file in /xyz, maybe called shortcut
in "shortcut", type
nautilus /abc/def

right click the file and set it as an executable. You may also change the emblems to make it look like a link. But now you need to  deal with the annoying "Do you want to run or display its contents?"

---

### Post by Primefalcon on 2011-02-09
ok..... full gui solution

click and hold the middle mouse button on what you want a shortcut to..... drag to where you want the shortcut to be, and release middle mouse button, an option window will appear asking you what to do... just select link here

a symbolic link (like a window shortcut), this "shortcut" can be to either files or folders

---

### Post by randiroo76073 on 2011-02-09
My way: In abc right clk def, make link = "link to def", right clk "link to def", cut, navigate to xyz, paste "link to def" rename if you want to "def". Has worked for yrs, maybe extra unnecessary steps, but that's me, has always added files/folders to original when put in link. That's all that concerns me.

---

