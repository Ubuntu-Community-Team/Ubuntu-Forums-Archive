---
title: "Print or save complete sources list?"
date: 2010-04-25
forum: General Help
---

### Post by bowens44 on 2010-04-25
I'm tying to find a way to print or export my entire sources list. /etc/apt/sources.list doesn't seem to be the full list.

Can some one tell me where this stored?

---

### Post by colorlessprism on 2010-04-25
you can very easily duplicate exactly what you have installed now on your new machine, open a terminal and type:
[FONT=Verdana]
[/FONT] [FONT=Verdana]sudo dpkg --get-selections | grep '[[:space:]]install$'| awk '{[COLOR=Black]print [/COLOR]$1}' > installedpackages
[/FONT] 
[FONT=Verdana]Now you should end up with a file called &#8220;installedpackages&#8221; it will be a long list of every package your currently have installed.[/FONT]

to restore from the previously exported package list use the following command (after making sure to also clone your /etc/apt/sources.list file)
 Update the source list using the following command
 
sudo aptitude update
 
Import the package list using the following command:
 
cat installedpackages | xargs sudo aptitude install

*Note: Without the same access to repositories it may not be able to find the packages.*

---

### Post by KeyserSoze93 on 2010-04-25
There are also some repositories listed in the directory  /etc/apt/sources.list.d, for example Medibuntu.

---

### Post by bowens44 on 2010-04-25
Thank you for your response. This is very good information to have but not quite what I'm looking for. I'm going to go to Lucid as soon as it's released and I want to keep track of the PPAs that I have added to my repository list  through synaptic so that I can easily find them and re-add them after the upgrade.

---

### Post by mike555 on 2010-04-25
might be easier just to open the list and take a screenshot of the list ........

---

### Post by gmargo on 2010-04-25
> keep track of the PPAs that I have added to my repository list   through synaptic I just added a ppa using Synaptic under 9.10 Karmic, and the line was added to the end of the **/etc/apt/sources.list** file.

---

### Post by jocko on 2010-04-25
As KeyserSoze93 said, the repos that are not listed in /etc/apt/sources.list are in separate files in the directory /etc/apt/sources.list.d/. Just copy the files to your home directory and back them up in any way you like.

---

