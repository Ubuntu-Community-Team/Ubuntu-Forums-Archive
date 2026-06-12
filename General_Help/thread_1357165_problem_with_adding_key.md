---
title: "problem with adding key"
date: 2009-12-16
forum: General Help
---

### Post by shaon3343 on 2009-12-16
[SIZE=2]**hi there, i am having problem with adding key of opera repository. ( deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) sid non-free) . i found a script by searching google ([http://popey.com/blog/2009/06/05/Easy_Script_To_Get_And_Install_PPA_GPG_Keys/)]("http://popey.com/blog/2009/06/05/Easy_Script_To_Get_And_Install_PPA_GPG_Keys/") which automatically add key if they ar not added before . and this script worked finely in my previous ubuntu 9.04. but in this ubuntu 9.10 it is not working. I also tried "sudo wget -O – [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add" . but no way . please help**[/SIZE]

---

### Post by shaon3343 on 2009-12-17
[B]hi all, 
I've got my solution!:D 

I ran these command: 

> [COLOR=Sienna]echo "deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free" | sudo tee -a /etc/apt/sources.list.d/opera.list && sudo apt-get update[/COLOR] 
and
> [COLOR=Sienna]wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -[/COLOR]
> [COLOR=Sienna]sudo apt-get install opera[/COLOR]

worked like charm!! :D

[/B]

---

