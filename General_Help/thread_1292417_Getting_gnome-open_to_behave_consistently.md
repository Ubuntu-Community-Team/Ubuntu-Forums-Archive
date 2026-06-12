---
title: "Getting gnome-open to behave consistently"
date: 2009-10-15
forum: General Help
---

### Post by jwbrase on 2009-10-15
The Windows way of determining which program to open a file with is to look at the extension and look up which program has been assigned to open that extension.

From what I understand, the standard way of doing things for Linux and other Unix-like OS's is to look at the contents of the file and see what application has been assigned to that particular data format.

Gnome-open however, seems to do some haywire combination of both. It will try (and fail) to open a jpeg with a .txt extension, the Windows way. But it will interpret a text file with a .gml extension as a plain text file, the Linux way. This is a problem because I have a certain program that uses machine-readable plain text files which it gives the extension .gml. But if I try associating that program with .gml files, all plain text files get opened with that program, which quickly chokes on the syntax of anything but its own files. And if I try associating other text files with gedit, .gml files get associated right along with them.

Is there any way to get *consistent* behavior out of Gnome-open, either to get completely content-based or completely extension-based associations? Even better (though I'm not holding my breath), is there any way to be able to associate things so that any difference in format or extension between two files causes them to be considered separate file types (Such that files with format 1 and extension .abc are opened with program A, files with format 1 and extension .xyz are opened with program B, and files with format 2 and extension .xyz are opened with program C)?

Failing that, are there any other file opening utilities available to replace Gnome-open that behave in a more sane fashion?

---

