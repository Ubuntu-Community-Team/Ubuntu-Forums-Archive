---
title: "Is it legal to create automatic Oracle JDK downloader?"
date: 2011-10-14
forum: General Help
---

### Post by riden on 2011-10-14
Hi folks,

Oracle recently has cancelled license for distributing JDK in linux distros and there are no way to install sun-java6-jdk and related packages. But installing it from Oracle it a kind of shame. So, there is idea to install Oracle JDK similar to Adobe Flash Player in Ubuntu (i.e. binary package will be downloaded from Oracle servers). But is such automatic installer legal?

---

### Post by ibutho on 2011-10-14
Best ask the people at Oracle (an email my help). I know its ok with flash and ms fonts, but not sure about Java.

---

### Post by jerry.west on 2011-10-14
No, it's not legal to bypass the Oracle site without Oracle's permission if the license forbids it.  That version of the JDK is not public domain, it belongs to Oracle.  If they have changed the license to forbid certain actions (such as redistributing binary packages) then you cannot legally do those things with any software to which that license applies.

But as you point out, for the user (or java programmer) it shouldn't be a problem. Your distro (presumably Ubuntu) will probably look to sort out some way to make it available to you just as they do for Flash.  And provided that downloads the JDK from the Oracle site and meets all the other requirements of the license, that will be fine.

However, if you need to re-distribute binary packages in some other form, you will have to move to one of the non-Sun (non-Oracle) versions such as IcedTea or GCJ.

Bottom line - unless you are a distro maintainer, it's not your problem :-).  Will Ubuntu do the right thing? I hope so, and expect so.
 
Hope this helps,
  Jerry

---

