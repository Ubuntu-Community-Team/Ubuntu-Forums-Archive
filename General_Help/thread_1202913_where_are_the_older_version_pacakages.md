---
title: "where are the older version pacakages"
date: 2009-07-02
forum: General Help
---

### Post by Its Me on 2009-07-02
Hi -

I recently installed openoffice3.1, long story short, I need to go back to openoffice 2.4. However, synaptic package manager does not have older version (2.4) of openoffice anmore.  Is there away to get the older OOo2.4 package? Openoffice download webpage only has RPM package available for 2.4, and I'm worried I'm too green to try an convert RPM package to DEBIAN given the Java JRE question. 

So, the simple solution, is there away to load the old 2.4 openoffice for ubuntu using synaptic manager (or apt-get)? 

thanks...

---

### Post by sdlynx on 2009-07-02
If you can find an Open Office repository that has the older version you can add it (System > Administration > Software Sources > Third Party Software) and then it should show up in SPM and you can install it from there.  Be careful though because many times these third party repositories aren't that great.

---

### Post by Its Me on 2009-07-02
I'm surprised that the older packages aren't kept around.  Seems kind of dangerous if some thing is wrong on the latest release of a new program, not to have older one still around.  Which is exactly what happened to me.   I'm really worreid now that I'm up creek with a paddle, as they say.

---

### Post by ajgreeny on 2009-07-02
I think Hardy 8.04 had OO2.4, so you may be able to get it from that repo, though it may give you a few dependency problems.  It may not, however, so give it a try.

---

### Post by Its Me on 2009-07-02
great news... but how do I get the Hardy (or even the Intrepid) repo  on synaptic (or apt-get)?  I'm really green at this? 

I did find source code for the openoffice2.4 release, but if I go down this path how do I make the source code excutable (compile with what software?).

---

### Post by michy99 on 2009-07-02
The Intrepid package is here:
 [CLICK HERE]("http://packages.ubuntu.com/intrepid/openoffice.org").
 Download at bottom of page.

---

