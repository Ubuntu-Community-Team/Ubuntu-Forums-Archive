---
title: "libreoffice-autocorrect"
date: 2011-07-18
forum: General Help
---

### Post by srisharan on 2011-07-18
I am from India.By default the language was set to English(India) in libreoffice.For some reason there is not auto correct.I have gone though all the settings changed everything to english USA.But still I get English India at the bottom and auto-correct is not working.Is there a way to change the language option to English usa so that auto correct will work.

---

### Post by bhadotia on 2012-01-11
> **srisharan said:**
> I am from India.By default the language was set to English(India) in libreoffice.For some reason there is not auto correct.I have gone though all the settings changed everything to english USA.But still I get English India at the bottom and auto-correct is not working.Is there a way to change the language option to English usa so that auto correct will work.

English (India) spell-check dictionary is not available in ubuntu. This is a known problem but unfortunately all bug reports regarding this were closed on launchpad and I have deleted my launchpad account (and don't want to make new one), so I cannot report the bug. Feel free to report this bug if you have a launchpad account. The closed bug which i was able to find is given below:
[1. Bug for OpenOffice]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/228555")

In the mean while, as you yourself point out, you can solve the problem by changing the default document language to English (USA). I think you must have changed the libreoffice language setting to English (USA) by going to the Tools>Options menu and the selecting the language for document as English (USA) under Language Settings>Languages tab. This will solve the problem for all the new documents you create using libreoffice.
For the documents you have already created using English (India) as the language may be you did not change the properties of the documents you're editing and may be thats the reason why you facing problems. To solve that:
Open the document.
Click on English (India) shown in the status bar and then choose English (USA) from the popup menu that appears.
Save the document and the document should now use English (USA) dictionary from now on.

---

