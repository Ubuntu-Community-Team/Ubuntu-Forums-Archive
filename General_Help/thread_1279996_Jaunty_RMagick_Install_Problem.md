---
title: "Jaunty RMagick Install Problem"
date: 2009-10-01
forum: General Help
---

### Post by frmontoya on 2009-10-01
I downloaded and installed imagemagick 6.5.6 and than I entered

$ sudo gem install rmagick

when I enter 

$ sudo irb -rubygems -r RMagick

I get 
/usr/lib/ruby/gems/1.8/gems/rmagick-2.11.1/lib/RMagick2.so:RuntimeError: This installation of RMagick was configured with ImageMagick 6.5.6 but ImageMagick 6.4.5 is in use.

Has anyone had this problem? Please let me know how I can fix this issue.

SOLVED:

I removed the source version of ImageMagick and reinstalled the packages. Everything installed correctly. I'll check to see if anyone replies and needs some help. Thanks.

---

