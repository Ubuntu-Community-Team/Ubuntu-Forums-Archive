---
title: "Setting up owncloud - switching from Xampp"
date: 2011-06-23
forum: General Help
---

### Post by avocado on 2011-06-23
Hi all,

I decided that owncloud looks very kewl, so I uninstalled apache friends' xampp which I've been using for years, and ran 'apt-get install owncloud'.
Install went fine, PHP, Apache, mySql all fine. I also added PHPmyadmin.

I can access my local html websites via localhost - but my Drupal sites ( I don't have any other dynamic sites so I don't know if it's Drupal related or database related exactly) only show the front page, but incomplete, and all links go to 404s.
I installed a fresh Drupal site no probs, it all works fine.

Could anyone suggest what I may have overlooked, please?

TFL.  :)

---

### Post by Blasphemist on 2011-06-23
From what you describe, didn't you loose your pre-existing drupal site databases and associated pages? It seems to me that you lost those sites by removing XAMP. I think a partial restore could be needed to get them back. Certainly you'd have to restore the databases but I'm not sure what else.

I no expert but do also have drupal 7 local. I too saw something about owncloud and am looking into building a site on a host, [https://www.packagecloud.com](https://www.packagecloud.com), and build a drupal 7 and owncloud site. Packagecloud says they think they can help if needed but didn't have any documents for me start from. They only have email support for now so I haven't decided on them just yet. My idea is to start with a site and cloud home for me and my friends and family.

---

### Post by avocado on 2011-06-23
Thanks for the quick reply, Blasphemist.

No, my files were unaffected by removing xampp, I backed-up all databases and have restored them via phpmyadmin.
I can access the front page of drupal sites, but no other pages.

Yes, I was looking at PackageCloud myself as an option.
I'm just trying to set it all up locally to start with.

---

### Post by avocado on 2011-06-24
Ahem.

Thanks for looking.
I've solved it.
I'm not even going to say what it was as no-one else would ever be daft enough to do this.

Cheers.
;)

---

