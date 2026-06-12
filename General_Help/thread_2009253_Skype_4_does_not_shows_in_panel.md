---
title: "Skype 4 does not shows in panel"
date: 2012-06-24
forum: General Help
---

### Post by Chelidze on 2012-06-24
So I installed Skype 4 in ubuntu and now it does not show icon it self in the top panel like it did
[IMG]http://i.imgur.com/XjZVf.png[/IMG]


this is how it looks now 

[IMG]http://i.imgur.com/ytQwd.jpg[/IMG]

is there a way to enable skype icon in the panel

      thank you for your time :)

and sry for my English



 Solved this with using this 

[askubuntu Bruno Pereira]("http://askubuntu.com/a/155434/42591")

Install the package `dconf-tools` by clicking on this button


or by opening a terminal and typing

    sudo apt-get install dconf-tools

Open `dconf-editor` and navigate to deskktop > unity > panel. On the systemtray-whitelist add Skype as one of the allowed applications

[IMG]http://i.stack.imgur.com/kDxil.png[/IMG]

---

