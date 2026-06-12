---
title: "bash &amp; xml"
date: 2011-11-04
forum: General Help
---

### Post by hyfanious on 2011-11-04
Hi, I am not so familiar with BASH coding
I just worked with PHP,JAVA Script(web-based programing)
I have a XML file
I need a bash code that can read ID attribute and related <Q> section and extract <Q>
 value related to the ID tag and do this for all parts of the XML file
how must be look like my while loop and my retrieving code?
thanks in advance

---

### Post by Lars Noodén on 2011-11-04
You're better off writing a program in Java or a script in Perl.  Both of those have libraries/modules well-designed for parsing XML.  

For perl, you have the [XML:: Parser](http://search.cpan.org/~msergeant/XML-Parser-2.36/Parser.pm) module and several others including [XML::TokeParser](http://search.cpan.org/~podmaster/XML-TokeParser-0.05/TokeParser.pm).

---

