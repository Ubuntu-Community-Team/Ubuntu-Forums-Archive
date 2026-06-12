---
title: "Latex for Tomboy won't install"
date: 2010-09-27
forum: General Help
---

### Post by zweiundzwei on 2010-09-27
I am trying to install the Latex addin for Tomboy. 
./configure now works, but then I get: 

```

doro@purple:~/Downloads/tomboy-latex-0.6$ make
Making all in src
make[1]: Entering directory `/home/doro/.local/share/Trash/files/tomboy-latex-0.6/src'
gmcs -debug -out:Latex.dll -target:library -resource:Latex.addin.xml -pkg:tomboy-addins -r:Mono.Posix Latex.cs LatexPreferences.cs LatexPreferencesFactory.cs
[COLOR="Red"]LatexPreferences.cs(7,37): error CS0246: The type or namespace name `Gtk' could not be found. Are you missing a using directive or an assembly reference?[/COLOR]
    Try using -pkg:gtk-sharp
Compilation failed: 1 error(s), 0 warnings
make[1]: *** [Latex.dll] Error 1
make[1]: Leaving directory `/home/doro/.local/share/Trash/files/tomboy-latex-0.6/src'
make: *** [all-recursive] Error 1

```

---

### Post by directhex on 2010-09-28
apt:tomboy-latex ?

---

### Post by zweiundzwei on 2010-09-28
Oh, oops. I did not realise this package exists. Thanks.

---

