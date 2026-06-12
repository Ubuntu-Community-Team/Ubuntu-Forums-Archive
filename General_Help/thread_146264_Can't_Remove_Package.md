---
title: "Can't Remove Package"
date: 2006-03-17
forum: General Help
---

### Post by dystrust on 2006-03-17
A few months ago I installed Lilypond and I didn't like it.  Ever since I've been trying to remove it.  I keep getting the following error message:

dpkg: error processing lilypond-data (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
dystrust@Mephisto:~$ Errors were encountered while processing:
 lilypond-data

How do I get rid of this package so that my updates will work properly?

---

### Post by mstlyevil on 2006-03-18
[QUOTE=dystrust]A few months ago I installed Lilypond and I didn't like it.  Ever since I've been trying to remove it.  I keep getting the following error message:

dpkg: error processing lilypond-data (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
dystrust@Mephisto:~$ Errors were encountered while processing:
 lilypond-data

How do I get rid of this package so that my updates will work properly?[/QUOTE]

Go to synaptic in System-->Administration-->Synaptic Package Manager. After you log in click on the search button and search for lilypond. In the display panel, right click on lilypond and select Mark For Reinstallation. Reinstall the package and then when it is done use Synaptic to remove the package.

---

### Post by dystrust on 2006-03-18
When I try that, this happens:

E: /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb: subprocess new post-removal script returned error exit status 1
E: /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb: subprocess pre-installation script returned error exit status 1

---

