---
title: "Where are repositories stored?"
date: 2010-04-06
forum: General Help
---

### Post by johnathanamber on 2010-04-06
Hello everyone!

It used to be before I used PPAs, I could clear the /etc/apt/sources.list file to get rid of repositories. However they are not in the list anymore. So in order to remove multiple repositories do I remove the files in the /etc/apt/sources.list.d folder?

Thank you and God bless,
Johnathan

---

### Post by johnathanamber on 2010-04-06
N/M, yes removing all of the files within the /etc/apt/sources.d folder does remove those same repositories from the Software Sources GUI.

Thank you and God bless,
Johnathan

---

### Post by dcstar on 2010-04-06
System-Administration-Software Sources

Do not manually edit files when perfectly good GUI tools exist to do the job properly.

---

### Post by johnathanamber on 2010-04-06
@dcstar,

It is understood that the GUI is available. However when you need to remove all of your repositories.... and you have literally 100s of them... the current GUI in Karmic, does not suffice.

To remove all of them via selecting each one individually and then clicking 'Remove' will take a while.

Removing all of the files in **/etc/apt/sources.list.d** was easier and took seconds.

I have tried using the GUI, **CTRL+LC** doesn't work. Do you have another suggestion?

I have a couple of suggestions for the GUI:
-Alphabetize the list (when you have errors, it is MUCH easier to look for them alphabetically rather than searching the entire randomized list)
-Allow to select multiple items.
-Option to auto-remove lists that end up with 'Not Found' as a result.

Thank you and God bless,
Johnathan

---

