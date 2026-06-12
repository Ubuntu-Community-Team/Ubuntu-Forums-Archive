---
title: "best way to install new softwares without internet"
date: 2009-09-15
forum: General Help
---

### Post by pravinbv on 2009-09-15
[CENTER][CENTER]**[COLOR=red][FONT=Verdana][SIZE=3]Best and Simplest way to install Softwares in Linux UBUNTU and MINT without internet connection:[/SIZE][/FONT][/COLOR]**[/CENTER]
[/CENTER]

[FONT=Verdana][SIZE=3]Please note that it is considered that you dont have internet on host pc but can go to internet cafe.[/SIZE][/FONT]

[FONT=Verdana][SIZE=3]Here are steps:[/SIZE][/FONT]

[FONT=Verdana][SIZE=3]1)[/SIZE]    [/FONT][FONT=Verdana][SIZE=3]Go to Software manager or Mint Install (not to synaptic packege manager, thats different)[/SIZE][/FONT]

[SIZE=3][IMG]http://ubuntuforums.org/C:%5CDocuments%20and%20Settings%5Cshree%5CMy%20Documents%5CMy%20Pictures%5C1[/IMG][/SIZE]

[FONT=Verdana][SIZE=3]2) Click on the software you want to install on ur pc. Here i want to install &#8220;FontForge&#8221; in Graphics category.[/SIZE][/FONT]
[FONT=Verdana][SIZE=3]It will give a short discription about the software you clicked. Now click on the &#8220;Install&#8221; button. [/SIZE][/FONT]
[FONT=Verdana][SIZE=3] [IMG]http://ubuntuforums.org/C:%5CDocuments%20and%20Settings%5Cshree%5CMy%20Documents%5CMy%20Pictures%5C2[/IMG][/SIZE][/FONT]


[FONT=Verdana][SIZE=3]3) When you click, the above window will appear. Again click on install button.[/SIZE][/FONT]
[FONT=Verdana][SIZE=3]When you click on 'install' button it will try to connect to internet and download neccesary packeges but it will fail and show error.[/SIZE][/FONT]


[FONT=Verdana][SIZE=3] [IMG]http://ubuntuforums.org/C:%5CDocuments%20and%20Settings%5Cshree%5CMy%20Documents%5CMy%20Pictures%5C3[/IMG][/SIZE][/FONT]
[FONT=Verdana][SIZE=3]4) In the error box all those required pagages will be given. Click in that box and copy all those links to a text file.[/SIZE][/FONT]
[FONT=Verdana][SIZE=3] [IMG]http://ubuntuforums.org/C:%5CDocuments%20and%20Settings%5Cshree%5CMy%20Documents%5CMy%20Pictures%5C4[/IMG][/SIZE][/FONT]

[SIZE=3][IMG]http://ubuntuforums.org/C:%5CDocuments%20and%20Settings%5Cshree%5CMy%20Documents%5CMy%20Pictures%5C5[/IMG][/SIZE]

[FONT=Verdana][SIZE=3]        5) Now by using find and replace function delete these lines [/SIZE][/FONT]
[FONT=Verdana][SIZE=3]        &#8220;W:Failed to fetch&#8221; and &#8220;Could not resolve 'archive.ubuntu.com' and save    the file with the name of Software.[/SIZE][/FONT]

[FONT=Verdana][SIZE=3]6)take that file to the computer with internet connection and copy paste the links. It will directly download the files. Save those files in a seperate folder with name of Software.[/SIZE][/FONT]

[FONT=Verdana][SIZE=3]        Please note that if you want to download many softwares, use seperate     folders with appropriate names otherwise your installation may give error     and many time this also happen that some of the dependancies required       by the software you want to install have already been satisfied by some    other related software which were not in the default intallation. So while    installing softwares, use the same sequence as that of you used to copy         the links in above manner.[/SIZE][/FONT]

[FONT=Verdana][SIZE=3]7)[/SIZE]    [/FONT][FONT=Verdana][SIZE=3]Now to install the software open the folders with the downloaded files. Open a new &#8220;Terminal Window&#8221;.  And browse to the folder with all those perticular software files. Here if have those three files in folder &#8220;Font Forge&#8221; i have to browse inside that folder. Use command &#8220;ls&#8221; without quotes. It should give you the list of files you have inside that folder. Now use these commands.[/SIZE][/FONT]

[SIZE=3][FONT=Verdana]>>            [/FONT][COLOR=red][FONT=DejaVu Sans Mono][FONT=Times New Roman]su[/FONT][/FONT][/COLOR][/SIZE]
[FONT=Verdana][SIZE=3]this will ask you your passward. Give it. And then use[/SIZE][/FONT]

[FONT=DejaVu Sans Mono][SIZE=3][FONT=Times New Roman]>>                    [COLOR=red]dpkg -i *.deb[/COLOR][/FONT][/SIZE][/FONT]

[FONT=Verdana][SIZE=3]this will install your software. If somehting goes wrong because of circular dependancies, you can use this command:[/SIZE][/FONT]

[FONT=DejaVu Sans Mono][SIZE=3][FONT=Times New Roman]>>                    [COLOR=red]dpkg -i --force-depends *.deb[/COLOR][/FONT][/SIZE][/FONT]


[FONT=Verdana][SIZE=3]This must install your new software. Use the same commands to install other downloaded software.[/SIZE][/FONT]

and the complete guide with images procedure is [here ]("http://www.ziddu.com/download/8656209/twaytoinstallsoftwareinlinuxwithoutinternet--guide.pdf.html")

---

### Post by Bonster on 2009-09-15
didnt no internet cafe has ubuntu linux now =)

but a faster way to do the above post is to use the synaptic.
demo video here [http://www.youtube.com/watch?v=0LmuQEVDznk](http://www.youtube.com/watch?v=0LmuQEVDznk)

---

