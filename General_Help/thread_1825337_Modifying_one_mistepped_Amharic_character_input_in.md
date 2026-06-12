---
title: "Modifying one mistepped Amharic character input in scim"
date: 2011-08-15
forum: General Help
---

### Post by EthioJOB on 2011-08-15
I use scim to type Amharic. While I find it great and very convenient, there is one minor issue I want to address. When I type "a" on the keyboard while in Amharic input, the result is supposed to be "&#4768;" (U+12A0). But instead, it shows "&#4771;" (U+12A3), which also appears when typed "A" on the keyboard. Is there a way I can fix this by editing some file or so? (see [http://www.geez.org/IM/sera-ez/sera-ez-am_ET.utf8.html](http://www.geez.org/IM/sera-ez/sera-ez-am_ET.utf8.html) for reference)

---

### Post by cruising on 2012-04-20
When I used Ubuntu 8.04, scim was amazingly smooth and 'just worked'! But when I tried to install it in Ubuntu 10.04, I had the same problem you had and spent hours trying to fix it. ](*,) Here's how it worked for me:\\:D/

[LIST=1]
[*]Go to synaptic and remove all installed packages of ibus, scim, and m17 (the culprit) :-x  You can easily do this by selecting to see the list of packages by "status" and choose "installed". You can then remove the three packages. I had to remove all three because after tinkering with my laptop and installing so many packages, I had to have a clean start.  
[*]Restart your computer and run in terminal "sudo apt-get update"
[*]Go back to Synaptic Package Manager and search for "scim" and mark it for installation and accept all of its dependencies. Also do a search for "scim-tables-additional" and "scim-modules-table" and mark them for installation. Since the Ethiopic (Ge'ez) website [http://keyboards.ethiopic.org/#SCIM]("http://keyboards.ethiopic.org/#SCIM") itself says that "M17N input methods implementations of the spec are available, however, while functional they are considered experimental at this time", DO NOT select anything m17, but stick to scim ONLY.
[*]Click "Apply", wait for installation to finish, and restart your computer. Then go to "System" >> "Preferences" >> "SCIM Input Method Setup" and click on "GTK" under "Panel". Choose "Always" under "Toolbar" for the "Show" option. I selected ALL the checkboxes on that window, with the exception of the two under "Input Window". I left those unchecked. 
[*] This should do it! 	:!: Please let me know if that helped. 
[/LIST]

---

