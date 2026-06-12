---
title: "After you install a program how do you run it if it doesn't show up in apps menu"
date: 2006-05-12
forum: General Help
---

### Post by jonnyfive on 2006-05-12
After you install a program how do you run it if it doesn't show up in apps menu?

I installed [Cinelerra]("http://heroinewarrior.com/cinelerra.php3") and I converted the rpm to deb and installed it, but it's not in the apps menu.

How do I run the program?
How do I add the program to the Applications menu?


Thank you

---

### Post by BobSongs on 2006-05-12
First open a Terminal:

 Applications > Accessories > Terminal

Then type in the name of the application you just installed. If the name is fairly long enough type a few of the letters (in this case cine) and hit the Tab key once or twice. This will then display a list of programs that begin with those letters (cine) and are ready to run. Or it may complete the name for you. You know you're ready to run if it places a space after the name auto-completes.

Once you've chosen what you want to run hit Enter.

To add the program to the Applications menu right-click the menu and click Edit Menus.

In the left pane choose the category where your application should be found. In this case: Sound and Video. Click Sound and Video and the list of applications currently available will appear in the right pane.

Click the New Entry button at the bottom middle of the Menu Editor. Give your application a name; then in the Command box fill in the name of the command that worked in the Terminal (perhaps **cinelerra** - remember case sensitivity!). Choose an icon (at this you're going to have to hunt, sorry).

Click OK then close the menu editor.

That's the quick and dirty.

---

### Post by harisund on 2006-05-12
(1) If you are familiar with the command line, you could go there, hit the first few alphabets of your application and hit tab. Hopefully the terminal will automatically complete it for you. 
(2) If you know exactly the name of the applicatoin (or you tried Step 1) you could hit Alt+F2 and in the dialog box enter the name of the application

---

### Post by jonnyfive on 2006-05-12
Thank you! That was awesome help. It worked great and you actually helped me to learn some more about linux!:KS

---

