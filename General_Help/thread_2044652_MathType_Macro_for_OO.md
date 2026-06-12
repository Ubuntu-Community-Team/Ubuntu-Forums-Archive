---
title: "MathType Macro for OO"
date: 2012-08-19
forum: General Help
---

### Post by thedoctor81877 on 2012-08-19
Hullo all. I am currently running Lubuntu 12.04, and using (though I had rather be using LaTeX-I have no choice in the matter-my new job requires MathType)MathType 6.8 I think. I was told that by inserting the following macro:

sub InsertMathTypeObject
rem ----------------------------------------------------------------------
rem define variables
dim obj   as object
dim SName as string
dim oXEO  as object
rem ----------------------------------------------------------------------
SName = "com.sun.star.text.TextEmbeddedObject"
obj = ThisComponent.createInstance(sName)
obj.CLSID = "0002CE03-0000-0000-C000-000000000046"
obj.attach(ThisComponent.currentController().Selection.getByIndex(0))
oXEO = obj.ExtendedControlOverEmbeddedObject
oXEO.doVerb(0)

end sub

I could then insert MT objects into OO. But so far, not only can I not go to Insert->Object->New->MT Object; but every time I try (copy and paste and manually typing it) to add the above macro, I get the following error:

BASIC runtime error.Object variable not set.

at the last line (oXEO.doVerb(0))

Pleas help. The only reason I 'ditched' LO and went 'back' to OO is that my local manager gave me the above code and said it was specifially for OO. If there is a similar macro for Lo, and I knew it would work, I would go back to that - but I am kind of stuck now, so any help is appreciated. Thanks.

---

### Post by sakamoto on 2012-08-19
you probably will have more chance being helped on the openoffice forums

---

### Post by thedoctor81877 on 2012-08-19
Ok, I shall try there as well. Thanks.

---

