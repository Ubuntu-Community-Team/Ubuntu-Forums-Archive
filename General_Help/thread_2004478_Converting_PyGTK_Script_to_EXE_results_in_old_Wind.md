---
title: "Converting PyGTK Script to EXE results in old Windows 2K GUI Look"
date: 2012-06-15
forum: General Help
---

### Post by gretty on 2012-06-15
My application gets the old Windows style/look when I compile my PyGTK Application into an .exe.


  **How I can I preserve the Windows XP GUI look and style when I compile my Python/PyGTK script with Py2Exe or PyInstaller?**
  

Is there a special .dll I need to include, do I need to create my own  .manifest file and link it in my Py2Exe script(if so how)? In Native  WinAPI I can toggle Windows XP style by using the function  InitCommonControls();, is there a PyGTK equivalent function that I can  use?


  Note: If I run my PyGTK script in the python interpreter then the GUI  has the correct Windows XP modern look. But when I compile that same  script into an .exe using Py2Exe or PyInstaller, the GUI of the .exe has  the old Windows 2K look and not the modern Windows XP look.


  *Any ideas on what I need to do to preserve the Windows XP look?*

---

