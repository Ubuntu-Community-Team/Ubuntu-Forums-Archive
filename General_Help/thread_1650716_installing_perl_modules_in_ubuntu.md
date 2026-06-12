---
title: "installing perl modules in ubuntu"
date: 2010-12-22
forum: General Help
---

### Post by dheerajkabra on 2010-12-22
Hi,

On fedora, I use perl-CPAN to install perl modules. It installs "cpan" command and its very easy to install perl modules from there.

what is the equivalent in ubuntu? I could not find anything in reference to cpan in my repos. Is there a new repo I need to add to my sources file?

-Thanks.

---

### Post by dheerajkabra on 2010-12-23
anyone ??

---

### Post by bt101 on 2010-12-23
I've used:

perl -MCPAN -e 'install modulename'
I do it as the root user.

You have to have perl installed of course.

Here's a link with more info.
[http://www.brandonhutchinson.com/installing_perl_modules.html](http://www.brandonhutchinson.com/installing_perl_modules.html)

---

### Post by gmargo on 2010-12-23
The **cpan** command is part of the **perl** package.
```

$ ls -l /usr/bin/cpan
-rwxr-xr-x 1 root root 11839 Jul 12 05:38 /usr/bin/cpan

```In any case, you most likely DO NOT want to install modules with the **cpan** command.  A great deal of CPAN modules are already packaged for ubuntu.  Use **apt-cache search** to help find them.  The packages all end in "-perl".

List all the -perl packages:
```

apt-cache search perl | grep -- -perl

```Search for one in particular:
```

$ apt-cache search HTML::Tree
libhtml-tree-perl - Perl module to represent and create HTML syntax trees
libhtml-scrubber-perl - Perl extension for scrubbing/sanitizing html
libhtml-treebuilder-xpath-perl - Perl module to add XPath support to HTML::TreeBuilder
libwww-mechanize-treebuilder-perl - Perl module integrating WWW::Mechanize and HTML::TreeBuilder
libxml-treebuilder-perl - XML parser providing XML::Elements DOM similar to HTML::Element

```Ah, there it is, the **libhtml-tree-perl** package.

---

