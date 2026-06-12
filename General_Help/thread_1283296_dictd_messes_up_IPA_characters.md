---
title: "dictd messes up IPA characters"
date: 2009-10-05
forum: General Help
---

### Post by tlknv on 2009-10-05
Hi All,
I have a problem with dictd in jaunty. International Phonetic Alphabet(IPA) characters look messes up. I don't think that there is a problem with my fonts or client. I can see the text from the dictd database file with all the IPA characters in the same terminal(uxterm) with the same font (DeJaVu Sans Mono). Also I see the proper IPA (in the same terminal under jaunty) running lenny's dictd through chroot from jaunty. I tried to use --locale=ru_RU.UTF-8 as well as --locale=en_US.UTF-8 and no locale at all ( I have LANG=en_US.UTF-8 ) for ditcd. I have all the mentioned locales installed and I don't forget to restart dictd. I tried to use another font which have IPA, English and Russian characters: Thryomanes. I tried to use different clients. I installed and checked all the versions of dictd <= jaunty from ubuntu repository. The result is always the same. I attached some screen shots:
file_ubuntu.png - that's what I see in the data file - the IPA look ok,
dictd_ubuntu.png - that's what I see with dict using ubuntu's dictd - the IPA messed up,
dictd_lenny.png - that's what I see with dict using lenny's dictd - the IPA look ok.
Any Ideas ?
Thanks,
Boris

---

