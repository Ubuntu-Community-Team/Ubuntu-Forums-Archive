---
title: "[eucalyptus]  Image store not working"
date: 2010-02-04
forum: General Help
---

### Post by Maarten90 on 2010-02-04
When I want to browse the image store in the web interface, I get the message 'Error 7: Couldn't connect to host'. [This]("https://bugs.launchpad.net/ubuntu/+source/eucalyptus/+bug/425926") Bug report tells me that the problem is fixed, but I am running the latest version of all the packages and it still tells me this. Why?

---

### Post by Maarten90 on 2010-02-07
*bump*

---

### Post by Maarten90 on 2010-02-08
It finally works. But when I download an image after a while it says:

> 
Command 'euca-upload-bundle' returned status code 1:
Checking bucket: image-store-1265658335
Traceback (most recent call last):
  File "/usr/bin/euca-upload-bundle", line 226, in <module>
    main()
  File "/usr/bin/euca-upload-bundle", line 209, in main
    bucket_instance = ensure_bucket(conn, bucket, canned_acl)
  File "/usr/bin/euca-upload-bundle", line 87, in ensure_bucket
    bucket_instance = connection.get_bucket(bucket)
  File "/usr/lib/pymodules/python2.6/boto/s3/connection.py", line 238, in get_bucket
    rs = bucket.get_all_keys(None, maxkeys=0)
  File "/usr/lib/pymodules/python2.6/boto/s3/bucket.py", line 204, in get_all_keys
    headers=headers, query_args=s)
  File "/usr/lib/pymodules/python2.6/boto/s3/connection.py", line 305, in make_request
    data, host, auth_path, sender)
  File "/usr/lib/pymodules/python2.6/boto/connection.py", line 419, in make_request
    return self._mexe(method, path, data, headers, host, sender)
  File "/usr/lib/pymodules/python2.6/boto/connection.py", line 398, in _mexe
    raise e
socket.error: [Errno 113] No route to host



This probably means the the DNS server is unable to resolve the domainname, but what domainname is it looking for?

---

### Post by thesheff17 on 2010-10-19
I am also having this same problem.  I have changed everything to br0 since this is recommended. I also hard coded cluster01 into my /etc/hosts file.  I'm going to see if that works.

This is on Ubuntu 10.10.  One machine is 32bit and 64bit but that shouldn't matter right?

---

### Post by vgokulakrishnan on 2011-03-04
Hi marteen,
                  Could u tell us how u overcame tat error abt Store tab, briefly,
I m getting 
"" ERROR 35: gnutls_handshake() failed: A TLS packet with unexpected length was received."
I tried purging and reinstalling python-image-store-proxy too, But didn't help.. [IMG]http://ubuntuforums.org/_3DLJna5PMuA3Kh92Lc9lpyyToc12piZKMaSJoc9lMl9zYm1Jql9zM1Eao1WJqi8vBp1[/IMG]
Any 1 has a solution, please say me asap..

---

