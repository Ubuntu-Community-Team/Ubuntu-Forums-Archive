---
title: "Problem with gtk/gdk assembly references in Monodevelop"
date: 2011-10-20
forum: General Help
---

### Post by alexp1010 on 2011-10-20
Hi,

I have a problem in Monodevelop (ver. 2.6) in Ubuntu 11.10.

When I create new Gtk# 2.0 project (New/Solution...) references like gtk-sharp, gdk-sharp and some others signed with errors "assembly not available for mono/.net3.5 (in mono 2.10.5)". 
When I click for gtk-sharp for example then Assembly browser opens with assembly's namespace and classes. 
When I try to build that solution warnings like "The reference 'gtk-sharp, Version=2.12.0.0, Culture=neutral,  PublicKeyToken=35e10195dab3c99f' is not valid for the target framework  of the project." 
and errors like "Error CS0246: The type or namespace name `Gtk' could not be found. Are you missing a using directive or an assembly reference? (CS0246)" appear. Images with error messages attached.

I have gtk-sharp2 installed. What can it be? How can I fix the problem?

Thanks in advance.

---

### Post by alexp1010 on 2011-10-22
Solved. 

I set Runtime Version to Mono/.Net4.0 in Project\Project Options\Build\General and project compiled well.

---

### Post by ovidiu_b13 on 2011-11-21
How did you do that? I can't find .NET 4.0

And I can't find any way to install it.

I have the same problem.

I'm using Ubuntu 11.10, and I've installed Mono from the repository.

---

### Post by StarNiell on 2012-04-14
Yes. It working, but only on Ubuntu (or Linux with mono). On Windows platform, with .NET 4.0 it not working!! Before... with .NET 2.0 (or .NET 3.5) target, the same application worked on Ubuntu and also on Windows platform (with Gtk#2 installed). How can resolve it without to install Mono 2.10 (about 79Mb!) on Windows Platform?

In alternative... I've been to build a clean installation of my application (for eg. with Inno Setup). Wath componets are needed to add to setup project?

Thanks for reply

---

