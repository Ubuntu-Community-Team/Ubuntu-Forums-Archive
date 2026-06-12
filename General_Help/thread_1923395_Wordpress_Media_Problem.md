---
title: "Wordpress Media Problem"
date: 2012-02-10
forum: General Help
---

### Post by gunksta on 2012-02-10
I installed Wordpress on my server and I can create text / formatted blog entries. But, I'm having trouble with using uploaded media. I am logged in as the site administrator. I can upload an image and save changes, but when I try to insert the image into a post, WordPress just freezes. I can log out and log back in and find the picture. The media uploads just fine, which makes me think my permissions are not the problem. (chmod -R 777) I just can't use the uploaded files.

Anyone have any experience fixing this?

I am self-hosting Wordpress on an old desktop that has been upcycled into a cheap server. It is running 11.10 and I am using the copy of WordPress from the repos.

Nothing fancy.

---

### Post by Dngrsone on 2012-02-11
Why use the Repos?  I always download WordPress straight from the site.

Who do you have set as owner of the Wordpress directory?  You should have it set to **www-data**, which will allow WP to do automatic updates and such.

---

### Post by gunksta on 2012-02-11
I tend to use software from the Ubuntu repos, so I don't have to worry about security updates. Some web stuff does a good job of automatically updating. Some does not. I usually think it is easier to use the stuff in the repos, rather than going solo, but that may not be the best approach in this case.

But, either way, using the repo software isn't my problem here. Over-all, WP appears to work properly. It just jams when I try to insert a picture into a post. It can upload / save the picture just fine (permissions appear to be fine for uploading at least).

---

### Post by gunksta on 2012-02-11
I looked at the folder where I had installed wordpress. I thought I had run chown on it, but apparently I did not, because wp-uploads was owned by www-data but the wordpress installation folder was not. Thanks.

Unfortunately, changing the ownership of the folder from root to www-data didn't appear to change the behavior of wordpress. Perhaps I should try installing from the web. This certainly isn't working.

---

### Post by gunksta on 2012-02-27
@_Dngrsone_

After fighting with this on and off again for several weeks, I finally tried installing from Wordpress directly. I should have done this earlier, since it resolved all of my problems.

Thanks

---

### Post by Dngrsone on 2012-02-27
> **gunksta said:**
> @_Dngrsone_

After fighting with this on and off again for several weeks, I finally tried installing from Wordpress directly. I should have done this earlier, since it resolved all of my problems.

Thanks

Glad you got it straightened out.

---

