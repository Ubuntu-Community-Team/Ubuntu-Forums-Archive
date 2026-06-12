---
title: "Adblock in Prism"
date: 2010-12-03
forum: General Help
---

### Post by woodpush on 2010-12-03
Hi I was googling for a while looking for a way to get Adblock working in Mozilla's Prism app. For anyone looking to do this, the steps are as follows:

1. Install Adblock in Firefox, if not already installed
2. Go to /home/your_name and press ctrl+h to show hidden folders.
3. Go to .mozilla/firefox/letters_and_numbers.default/extensions. In there, there should be a folder with a long name. In my case it was {d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}. This folder should contain the adblock extension.
4. Copy this folder and paste it into /home/your_name/.mozilla/extensions/prism@developer.mozilla.org
5. Restart Prism and it should prompt for you to select an ad filter. You may need to recreate your shortcuts again for the addon to be recognised. That's it!

This may work for other addons but I have not tested it.

---

