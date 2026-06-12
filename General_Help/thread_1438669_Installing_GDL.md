---
title: "Installing GDL"
date: 2010-03-25
forum: General Help
---

### Post by Hugh Bown on 2010-03-25
I am a beginner. I have installed Ubuntu (dual boot mode with Windows XP) and read Keir Thomas's very helpful "Ubuntu Pocket Guide and Reference, and made a donation.

I need to install and use GDL.

( I have got a bit further since I last edited this post and my latest output is tacked on at the end of this)

I have a directory which I downloaded to my desktop gdl-0.9rc4 , it has 5 sub-directories (doc, m4, src, templates and testsuite) There is a README file which does not help with installing.

The furthest I have got is as per the list below.

I suspect I should delete gdl-0.9rc4 and start again.

Plenty of people have installed GDL. A simple line by line account right from the beginning would be much appreciated.

I have tried ~/Desktop/gdl-0.9rc4$ .configure 
and just get the message that gdl-0.9rc4$ is a directory
Yet I notice that in a previous thread in (hamburglar6 16th June 2007)
"gdl-0.9pre4$ ./configure"
proceeded to produce a long response



-----------------------------------------------------------------------------

hugh@ubuntu:~/Desktop/gdl-0.9rc4$ sudo apt-get install gdl
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gdl

I then got a message that I should load gnudatalanguage which I did.
I got a lot of messages ending in 
"Setting up gnudatalanguage (0.9~rc1-1.1ubuntu2.1) ..."
No indications of "error" in the process.
But nowhere nearer installing GDL

Latest Output

GDL - GNU Data Language, Version 0.9
For basic information type HELP,/INFO
'GDL_STARTUP'/'IDL_STARTUP' environment variables both not set.
No startup file read.
GDL> 

So I seem to have got gnudatalanguage installed now, but how do I go from here ? I have a GDL model from another researcher it has several directories and sub directories. One of the latter is entitled "Model" but I don't know what I should type at the GDL> prompt. I have tried a few things.

---

### Post by Senplanet on 2011-01-02
> 
'GDL_STARTUP'/'IDL_STARTUP' environment variables both not set.
No startup file read.
[SIZE=1]
First of all ,you have to set the environment for your GDL[B]

The way how to do it :
[http://www.physics.emory.edu/students/kdesmond/SettingUpGDL.html](http://www.physics.emory.edu/students/kdesmond/SettingUpGDL.html)
[/B][/SIZE]

---

