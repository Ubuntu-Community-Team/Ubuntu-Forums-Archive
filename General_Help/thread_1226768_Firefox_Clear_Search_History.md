---
title: "Firefox Clear Search History"
date: 2009-07-29
forum: General Help
---

### Post by cj100570 on 2009-07-29
This has bothered me for a while now. Why is it that the Ubuntu version of Firefox doesn't have an option to "Clear Search History" in the search bar like the Windows version? Is there a way to edit the Firefox configurations files to enable this?

---

### Post by Tamlynmac on 2009-07-29
I also noticed this and implemented this as a solution.

Install the Toolbar Buttons (0.6.0.5) extension from Mozilla Firefox Addons

Once installed go to view/toolbars/customize and locate the "clear data" lock icon and add it to your Firefox toolbar.

Setup which Private Data (edit/preferences/Privacy/Private Data Settings) you wish to clear/erase.

The only issue with this, is if you should choose to clear different private data when closing Firefox versus when clicking the lock icon in your toolbar.

Good Luck and Hope This Helps

---

### Post by cj100570 on 2009-07-29
> **Tamlynmac said:**
> I also noticed this and implemented this as a solution.

Install the Toolbar Buttons (0.6.0.5) extension from Mozilla Firefox Addons

Once installed go to view/toolbars/customize and locate the "clear data" lock icon and add it to your Firefox toolbar.

Setup which Private Data (edit/preferences/Privacy/Private Data Settings) you wish to clear/erase.

The only issue with this, is if you should choose to clear different private data when closing Firefox versus when clicking the lock icon in your toolbar.

Good Luck and Hope This Helps

Thanks. I'm trying to avoid using add-ons to gain this functionality. I already have Firefox clearing private data when I close it so I don't need anything that duplicates that.

---

### Post by Tman5293 on 2009-07-29
Go to Tools>Clear Private Data

---

### Post by cj100570 on 2009-07-29
> **Tman5293 said:**
> Go to Tools>Clear Private Data

I'm not trying to clear private data. I want to enable the option of clearing search history from within the search box. It's an option in Windows but it's greyed out in Linux.

---

### Post by pjcdawkins on 2009-08-20
It's because you've disabled the option "Remember what I enter in forms and the search bar" in Edit -> Preferences -> Privacy.

When it's disabled, Firefox doesn't keep a history in your search bar at all - apart from leaving the last thing you type there (a little bit annoying but not quite a bug IMO)  - so 'clear search history' is greyed out. So just enable the option again, or select that text and delete it.

I don't know how it behaves in Windows - try it while keeping an eye on the privacy settings of both browsers.

---

### Post by cj100570 on 2009-08-20
> **pjcdawkins said:**
> It's because you've disabled the option "Remember what I enter in forms and the search bar" in Edit -> Preferences -> Privacy.

When it's disabled, Firefox doesn't keep a history in your search bar at all - apart from leaving the last thing you type there (a little bit annoying but not quite a bug IMO)  - so 'clear search history' is greyed out. So just enable the option again, or select that text and delete it.

I don't know how it behaves in Windows - try it while keeping an eye on the privacy settings of both browsers.

Thanks for your reply. I do indeed have that checked because I don't want my searches saved. However, they are still saved since, as you pointed out, the last thing typed into the search box remains and there's no way to remove it. I guess I'll just have to live with it.

---

