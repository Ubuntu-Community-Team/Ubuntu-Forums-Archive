---
title: "Confused over groups: accessing www-data files from Windows"
date: 2012-01-31
forum: General Help
---

### Post by 5circles on 2012-01-31
I'm trying to edit files on my Ubuntu development server using Windows tools.  The files are owned by www-data, group www-data also.  I had problems after changing this, so I'd like to stick with the ownership if possible.  My user is in the www-data group.


I can map a drive to the Ubuntu machine as my own user, but unless I change group permissions to allow write I can't edit files.  I don't know if this will mess things up once I start putting the files on the internet.

I can't map a drive as www-data, even after adding a password.

Is there a good strategy for owner and group permissions that will not let me mess up for files copied to the internet?

Thanks
Mike

---

