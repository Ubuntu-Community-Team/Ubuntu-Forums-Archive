---
title: "Thunderbird unset 80 chars width lines?"
date: 2011-01-25
forum: General Help
---

### Post by fmmarzoa on 2011-01-25
Hello,

For some reason it seems like my Thunderbird 3.x has a limit of 80 chars per line enabled, so when I edit a message, it puts a line feed on or before that limit.

I think it could be set when I installed Enigmail for using GPG, that changes some default values, but I'm not sure.

Anyway I would like to avoid this issue, so I can write lines as long as I want, but I've not found a configuration option to do this within "Preferences" dialog.

Do you know where it is?

Thanks,

---

### Post by SeijiSensei on 2011-01-25
It used to be visible in the Composition settings, but it's not there any more.  Instead, go to Edit > Preferences > Advanced and click the "Config Editor" button.  In the box that appears, type "wrap" in the search box at the top.  I think the mailnews.wraplength parameter controls plain-text messages, while the editor.htmlWrapColumn setting controls HTML widths.

---

