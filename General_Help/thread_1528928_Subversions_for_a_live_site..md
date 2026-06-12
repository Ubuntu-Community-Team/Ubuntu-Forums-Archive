---
title: "Subversions for a live site."
date: 2010-07-11
forum: General Help
---

### Post by Antexter on 2010-07-11
I'm setup on a virtual dedicated server with a host running ubuntu, but I'm trying to setup subversions.

Now I can set it up in say /svn/myrepository

But I want to set it up on one of my websites e.g.

/var/www/vhosts/example.com/httpdocs
but when i run svnadmin create on httpdocs i get the following error.

svnadmin: Repository creation failed
svnadmin: Could not create top-level directory
svnadmin: 'httpdocs' exists and is non-empty

am I going about this all wrong?

---

### Post by Antexter on 2010-07-11
I think I got a little further instead I made a new folder /var/svn/example.com

I also made /var/svn/autoupdate/autoupdate.c with:

#include <stddef.h>
#include <stdlib.h>
#include <unistd.h>
int main(void)
{
  execl("/var/svn/example.com", "svn", "update",
"/var/www/vhosts/example.com/httpdocs/test",
        (const char *) NULL);
  return(EXIT_FAILURE);
}


and I've compiled that and ran it but it will not merge my files.
I've basically been following this: [http://www.frenssen.be/content/using-subversion-automatically-update-live-website](http://www.frenssen.be/content/using-subversion-automatically-update-live-website)

---

