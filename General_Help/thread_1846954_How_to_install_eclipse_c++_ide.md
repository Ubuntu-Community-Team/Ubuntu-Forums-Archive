---
title: "How to install eclipse c++ ide?"
date: 2011-09-19
forum: General Help
---

### Post by vikash_chandola on 2011-09-19
there are two download links in their [download section]("http://www.eclipse.org/downloads/"). which one should i download.

---

### Post by papibe on 2011-09-19
Have you tried the version on the Software Center?

There's also the extra 'clipse-cdt' package (features and plugins that are useful for C and C++ development).

Regards.

---

### Post by raja.genupula on 2011-09-19
get the first one from that . i think first one includes all the things you need .

---

### Post by arka.sharma on 2011-09-20
Download the cdt plugin for eclipse.Extract it.There would be two directories inside extracted folder.One called features one plugins.Inside plugin directory there would be jar files.Copy them and paste inside "your eclipse installation directory/plugins" directory.Similarly copy the contents of "extracted folder/features" to "your eclipse installation directory/features".Then restart eclipse.Hope this should work.

---

### Post by vikash_chandola on 2011-09-20
> 
Have you tried the version on the Software Center?

There's also the extra 'clipse-cdt' package (features and plugins that are useful for C and C++ development).

Regards.
Hello!
My operating system is not fixed. I used to switch OS in a week(most long a month). So installing it through software center is not a good idea for me.
thanks for Help.


> 
get the first one from that . i think first one includes all the things you need .     
namaste
downloading first one. Will it work as it work in windows(no installation require) or i need to install??????

> 
Download the cdt plugin for eclipse.Extract it.There would be two  directories inside extracted folder.One called features one  plugins.Inside plugin directory there would be jar files.Copy them and  paste inside "your eclipse installation directory/plugins"  directory.Similarly copy the contents of "extracted folder/features" to  "your eclipse installation directory/features".Then restart eclipse.Hope  this should work.     namaste 
let me download 
After that see your answer.

---

### Post by raja.genupula on 2011-09-20
yeah but for first its gonna take  more time and then next time on wards no such issues . you should have JRE environment to run that one make sure about it . 

all the best

---

### Post by vikash_chandola on 2011-09-20
> **raja.genupula said:**
> yeah but for first its gonna take  more time and then next time on wards no such issues . you should have JRE environment to run that one make sure about it . 

all the best
Is it that java runtime that i need. (require to run eclipse)

---

### Post by lkjoel on 2011-09-20
Try this:
```
sudo apt-get install eclipse-cdt
```

---

### Post by raja.genupula on 2011-09-20
yeah go with that 
all the best

---

### Post by vikash_chandola on 2011-09-20
hey guys good news is  that it is working but bad news is that, that i can't use it.
See screen shot.
why it is showing error for cout.
I have already installed GNU GCC compiler. codeblocks using that compiler it works fine then why not eclipse. When i create project everything(setting) seem correct.

---

### Post by lkjoel on 2011-09-20
Try this: [http://lkubuntu.wordpress.com/2011/07/12/upgrading-eclipse-to-3-7/](http://lkubuntu.wordpress.com/2011/07/12/upgrading-eclipse-to-3-7/)

---

### Post by vikash_chandola on 2011-09-20
> **vikash_chandola said:**
> hey guys good news is  that it is working but bad news is that, that i can't use it.
See screen shot.
why it is showing error for cout.
I have already installed GNU GCC compiler. codeblocks using that compiler it works fine then why not eclipse. When i create project everything(setting) seem correct.


done.
i have solved problem.
I need to select 3rd one option in compilers. that is helllo world C++ project..
So i am going to start going to learn C++ programming. Hope i will complete it soon.
thanks to **raja, lkjoel & arka.sharma** for helping.
keep helping guys.

---

