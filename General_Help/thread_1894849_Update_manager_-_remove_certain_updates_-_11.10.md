---
title: "Update manager - remove certain updates - 11.10"
date: 2011-12-13
forum: General Help
---

### Post by athreya86 on 2011-12-13
Is there a way to suppress certain updates in the update manager on 11.10? For example, I don't use evolution - I don't want to download and install updates related to evolution. So, I'd like to suppress updates related to evolution such that I don't get any notifications related to evolution.

---

### Post by pretty_whistle on 2011-12-13
> **athreya86 said:**
> Is there a way to suppress certain updates in the update manager on 11.10? For example, I don't use evolution - I don't want to download and install updates related to evolution. So, I'd like to suppress updates related to evolution such that I don't get any notifications related to evolution.
Go to Synaptic and do a search for the program.  Highlight it, then go to Packages and hit "Lock version".

That's it.

---

### Post by yetiman64 on 2011-12-13
pretty_whistle's idea sounds good.

If you haven't got Synaptic available, in a terminal ```
sudo apt-get install synaptic
```will sort that.

Just something to think about, other applications may be accessing the libraries etc locked down from being updated. I'd suggest you only lock down the main package and not packages like evolution-data (one I have seen associated with other programs, dependency wise).

Just checked evolution is not installed here in 11.10, Thunderbird is now the default install, it appears you will be locking down packages used by other applications OP.

---

