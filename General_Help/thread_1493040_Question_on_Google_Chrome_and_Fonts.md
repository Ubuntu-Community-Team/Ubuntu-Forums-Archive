---
title: "Question on Google Chrome and Fonts?"
date: 2010-05-25
forum: General Help
---

### Post by sports fan Matt on 2010-05-25
I am using Franklin Gothic Medium Condensed for my webpages and I really like it.  Except in Google Chrome, if I am typing a heading (to the naked eye) it does not look like it, it looks like another font.  Is this standard behavior?  

The difference between the title and text in the space provided to me looks different.  Is it me, or am I just seeing things that no one else can?

---

### Post by sports fan Matt on 2010-05-25
I don't know if you can force a particular font family, but it's easy to try.  I want to do just that.  It then should be able to read the defualt font as x (whatever x is) but how?

---

### Post by fragos on 2010-05-25
You control what fonts are displayed in a web site in the referenced CSS file. For example to set the font for an entire page:

body {
	font-family:"DejaVuSansCondensed", "Tahoma", "Arial", "Helvetica", "Garuda", sans-serif;}

You'll note that I've listed a series of font options. The reason is that browsers use the fonts already installed on the user's PC. You may have that font on your PC but site visitors are unlikely to and default to a generic like "sans-serif." Microsoft has a proprietary markup allows you to include a copy of a font with the site. This only works with IE. [http://FragosTech.com]("http://FragosTech.com") has a lot of how to information on building web sites.

---

