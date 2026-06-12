---
title: "Documents in Gnome Shell Favorites"
date: 2012-02-02
forum: General Help
---

### Post by forrestcupp on 2012-02-02
I have a document that I regularly use with LibreOffice. Is there any way to put a direct launcher to that document in the favorites bar in Gnome Shell? I noticed that when that document is opened, the right-click menu of the LibreOffice Writer favorites icon lists it. I wish there were a way to pin it there, like in Windows 7. But I'd be satisfied if there is at least a way to put a separate launcher that directly opens that document.

---

### Post by forrestcupp on 2012-02-02
I found [this extension for Gnome Shell](https://extensions.gnome.org/extension/33/jump-lists/) that adds Zeitgeist powered jumplists to the favorite launchers. It doesn't look like you can pin things to it permanently, but at least you can open documents from a list of recently opened documents. That's a lot better than nothing.

---

### Post by Frogs Hair on 2012-02-02
I created a Nautilus Root launcher and I am able to add it to the Unity launcher , but it reverts to a home folder shortcut when placed on the Gnome shell favorites panel . It works from the applications menu though . I think I remember seeing a favorites extension .

---

### Post by forrestcupp on 2012-02-06
For future reference, and if anyone ever needs to know how to do what I originally wanted to do, I finally figured out how to add a launcher to a document to Gnome Shell's Dash favorites.

First, I created a script that opens the document that I want a favorite for. Since I'm using Lotus Symphony, my script in a text file looked something like this:
```
symphony ~/path/filename
```Then I made the text file executable. Since I'm a GUI guy, I just right-clicked the file, went to properties, clicked the Permissions tab, and checked the Execute box.

Then in a terminal, I entered the following:
```
gnome-desktop-item-edit ~/.local/share/applications/ --create-new
```
In the window that comes up, make sure **Application** is the type, enter the name for the launcher, enter the command to launch your script, and a comment description. Make sure to change the icon before you press OK, or it won't have any icon. All of this will allow your launcher to show up in a Dash search.

Now you can go to Gnome Shell's Dash and type in the name of the launcher you just created. When it shows up in the search, right-click it and choose to add to your favorites.

It's a lot harder than it should be, but at least it works.

Edit:
I found out that you don't have to make a script. I was able to just put the symphony command into the launcher creation, and it worked. For some reason, I had to use the whole /home/username path because ~/ didn't work.

---

