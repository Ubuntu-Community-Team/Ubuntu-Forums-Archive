---
title: "S3curl Digest/HMAC_SHA1 error"
date: 2010-06-17
forum: General Help
---

### Post by dragos2 on 2010-06-17
I am trying to use s3curl.pl and it gives this error in Ubuntu 10.04:

```

Can't locate Digest/HMAC_SHA1.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at ./s3curl.pl line 18.
BEGIN failed--compilation aborted at ./s3curl.pl line 18.

```

In the source it says:
```

use strict;
use POSIX;

# you might need to use CPAN to get these modules.
# run perl -MCPAN -e "install <module>" to get them.

use Digest::HMAC_SHA1;
use FindBin;
use MIME::Base64 qw(encode_base64);
use Getopt::Long qw(GetOptions);

```

Since I don't know perl how do I install what I miss ?

---

### Post by dragos2 on 2010-06-18
Bump.

---

### Post by jdillaczek on 2010-06-18
I got the same error; installing the libdigest-hmac-perl package fixed it for me:

> $ sudo apt-get install libdigest-hmac-perl

---

### Post by dragos2 on 2010-06-21
> **jdillaczek said:**
> I got the same error; installing the libdigest-hmac-perl package fixed it for me:

Thank you.

I think it can be fixed with this too but not sure about the exact command:
```

perl -MCPAN -e "install <hmachere>"

```

---

