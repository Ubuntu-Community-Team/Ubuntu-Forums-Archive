---
title: "Installation of Vim ubuntu 9.10"
date: 2009-12-15
forum: General Help
---

### Post by jabe_z on 2009-12-15
Hi, I'm new to Linux. I just installed Ubuntu 9.10.

I use Gvim as my preferred file editor. I use lot of scripts for customizing Gvim editor on windows. Normally in windows i keep all those scripts in Vim folder which is in program files. 

location of All Vimscripts : C:\programfiles\vim\vim72\vimfiles\...
location of vimrc : C:\programfiles\vim\vim72\vimrc
location of gvimrc : C:\programfiles\vim\vim72\gvimrc

I want to move all those scripts on to Ubuntu. Where should i place all these scripts?? When i searched for the files to place, i found several places where Gvim files are present. I found them in 
/usr/share/vim
/usr/local/vim
/etc/vim

so i'm confused. Please help me to put all the customization scripts. 
---------------------------------------------------------------
I've some general questions.
1. where can i find the files which are installed on Ubuntu?? 
2. Where are all the libraries found in developing any application? 
3. How can i patch the applications??

Please pardon me if this is already asked. I did googling before posting this question.

Thanks in advance.

---

### Post by redmk2 on 2009-12-15
> **jabe_z said:**
> Hi, I'm new to Linux. I just installed Ubuntu 9.10.

I use Gvim as my preferred file editor. I use lot of scripts for customizing Gvim editor on windows. Normally in windows i keep all those scripts in Vim folder which is in program files. 

location of All Vimscripts : C:\programfiles\vim\vim72\vimfiles\...
location of vimrc : C:\programfiles\vim\vim72\vimrc
location of gvimrc : C:\programfiles\vim\vim72\gvimrc

I want to move all those scripts on to Ubuntu. Where should i place all these scripts?? When i searched for the files to place, i found several places where Gvim files are present. I found them in 
/usr/share/vim
/usr/local/vim
/etc/vim

so i'm confused. Please help me to put all the customization scripts. 
---------------------------------------------------------------
I've some general questions.
1. where can i find the files which are installed on Ubuntu?? 
2. Where are all the libraries found in developing any application? 
3. How can i patch the applications??

Please pardon me if this is already asked. I did googling before posting this question.

Thanks in advance.

Your own customization goes in your home directory (e.g. ~/).

See [**_[COLOR="DarkSlateGray"]here [/COLOR]_**]("http://vim.sourceforge.net/scripts/script_search_results.php?order_by=creation_date&direction=descending")for scripts.

---

### Post by jabe_z on 2009-12-15
Thanks for your reply. But i dont see any files or folders in home directory. May be i am in wrong folder. If the home directory you mentioned is "Gvim's Home directory", i couldn't find its home directory :( :( :(. 

I'm completely new to Ubuntu and dont know anything about its files and folders structure :( :(:( 

Regarding scripts, I already have some scripts which i use everyday. Thank you.

---

### Post by xifer on 2009-12-15
> **jabe_z said:**
> Thanks for your reply. But i dont see any files or folders in home directory. May be i am in wrong folder. If the home directory you mentioned is "Gvim's Home directory", i couldn't find its home directory :( :( :(. 

I'm completely new to Ubuntu and dont know anything about its files and folders structure :( :(:( 

Regarding scripts, I already have some scripts which i use everyday. Thank you.

when you first open a terminal window you should be in your default home directory.

This is referred to with a tilda character

to list files in your home folder you can enter this:

ls ~


or to see more info on hidden files

ls -xal 


to check your current working directory (print which directory)

pwd

to set (change current working directory)

cd /home/someotheruser

custom file for vim might be something like

/home/someusername/.vim/vim.conf


To apply for all users you may have

/user/share/vim/vim.conf

or 

/etc/vim/vim.conf

and so on

1. cd /
ls -lR
2. that's up to the developer /lib has many common libararies
3. depends on the application - edit the source, build the objects...

---

