---
title: "loosing Thunderbird AddressBooks"
date: 2012-07-07
forum: General Help
---

### Post by garydale on 2012-07-07
This is getting painful. Some time before upgrading from Ubuntu 10.04 to Ubuntu 12.04 my address books stopped working. I ended up deleting the abook.mab and history.mab files to get it working again.

Now it's happened again. The address books are there (the abook.mab and history.mab files) but Address Book shows them as empty and won't let me add to to them, let alone collect the addresses. Starting Thunderbird in safe mode doesn't help either. Ditto for starting just the address book.

When I remove the current .mab files (rename them to .save), Thunderbird creates new ones which work (but are empty). It also gives me two entries each for Personal Address Book and Collected Addresses. I can't delete the extra entries - Thunderbird gives a message about Evolution integration.

If I remove the new (working but empty) books and replace them with the old (.save) ones,I lose mention of the Personal Address Book and Collected Addresses and am left with just "Personal" (possibly a relic of the last time I was trying to fix the problem) and "Ubuntu One", which are empty and non-functioning.

Any ideas on what's going on and/or how to fix it?

---

### Post by ajgreeny on 2012-07-07
It sounds as if your TB profile is corrupt.

Rename the hidden **.thunderbird** folder in your home as **.thunderbirdbackup** then restart TB to remake the hidden folder.  You can try copying across the Mail subfolder from your old profile to get any downloaded mail, and could also try restoring other subfolders and files until you find the problem re-occurs.

Once you have everything running as you want it, it's always worth exporting your addressbook contacts as a csv or ldif backup file for just such strange happenings.

---

