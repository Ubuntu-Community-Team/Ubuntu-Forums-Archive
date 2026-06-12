---
title: "Why does plugin-container use so much RAM?"
date: 2011-07-01
forum: General Help
---

### Post by jejones3141 on 2011-07-01
When I use firefox, I accumulate multiple plugin-container processes, typically one of them sits around hanging onto well over 200 MB of RAM. I think this happens when I watch flash videos. Does simply having a flash app on a web page cause a plugin-container process to be created? Will they ever go away without my explicitly killing them or closing firefox? If they stay around, do they ever free any RAM?

---

### Post by Gryllida on 2011-07-02
**- Does simply having a flash app on a web page cause a plugin-container process to be created?**
Yes.

**- Will they ever go away without my explicitly killing them or closing firefox?**
Yes - if you close a tab with a page which uses Flash, its plugin-container processes disappear.

**- If they stay around, do they ever free any RAM?**
Generally yes, but this depends on how the Flash application you are using works.

More details: 
- [What is plugin-container](http://support.mozilla.com/en-US/kb/What is plugin-container)
- [Performance or display issues with certain Flash videos // MozillaZine](http://kb.mozillazine.org/Flash#Performance_or_display_issues_with_certain_Flash_videos)
- [How to disable plugin-container](http://kb.mozillazine.org/Plugin-container_and_out-of-process_plugins#Disabling_crash_protection) - this will switch to running all plugins inside of Firefox process, like it was before Firefox 3.6.4.

---

