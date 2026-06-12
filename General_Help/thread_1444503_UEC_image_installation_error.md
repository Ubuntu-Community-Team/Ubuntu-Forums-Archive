---
title: "UEC image installation error"
date: 2010-04-01
forum: General Help
---

### Post by varunpandeyengg on 2010-04-01
I recently installed Ubuntu Enterprise Cloud (UEC) on two of my machines - CC & NC both. I was trying to install the store image through WebUI. I was able to download Ubuntu 9.10 - Karmic Koala (i386) image but while installing, it's giving me following error: -
-------------------------------------------------------------------------------------------------------------------------------------------------------------
Command 'euca-upload-bundle' returned status code 1:
Checking bucket: image-store-1269025279
Traceback (most recent call last):
  File "/usr/bin/euca-upload-bundle", line 226, in
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
socket.error: [Errno 110] Connection timed out
------------------------------------------------------------------------------------------------------------------------------------------------------------
 Please Help me with this. Thanks in advance :-)

---

### Post by Chewbranca on 2010-05-15
Any luck with this? I'm running into the same issue. I can't install any of the store images on UEC 10.04, getting the same timeout issue. I get this on any of the images I try and install. Any help would be greatly appreciated.

---

### Post by Chewbranca on 2010-05-15
I get the same error when I try to manually bundle as described here: [https://help.ubuntu.com/community/UEC/BundlingImages](https://help.ubuntu.com/community/UEC/BundlingImages)


--2010-05-15 18:43:41--  [http://uec-images.ubuntu.com/lucid/current//lucid-server-uec-amd64.tar.gz](http://uec-images.ubuntu.com/lucid/current//lucid-server-uec-amd64.tar.gz)
Resolving uec-images.ubuntu.com... 91.189.88.35
Connecting to uec-images.ubuntu.com|91.189.88.35|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 201223675 (192M) [application/x-gzip]
Saving to: `lucid-server-uec-amd64.tar.gz'

100%[====================================================>] 201,223,675 1.30M/s   in 1m 45s  

2010-05-15 18:45:27 (1.82 MB/s) - `lucid-server-uec-amd64.tar.gz' saved [201223675/201223675]

Sat May 15 18:45:27 PDT 2010: ====== extracting image ======
Warning: no ramdisk found, assuming '--ramdisk none'
kernel : lucid-server-uec-amd64-vmlinuz-virtual
ramdisk: none
image  : lucid-server-uec-amd64.img
Sat May 15 18:45:41 PDT 2010: ====== bundle/upload kernel ======
Traceback (most recent call last):
  File "/usr/bin/euca-upload-bundle", line 231, in <module>
    main()
  File "/usr/bin/euca-upload-bundle", line 214, in main
    bucket_instance = ensure_bucket(conn, bucket, canned_acl)
  File "/usr/bin/euca-upload-bundle", line 87, in ensure_bucket
    bucket_instance = connection.get_bucket(bucket)
  File "/usr/lib/pymodules/python2.6/boto/s3/connection.py", line 275, in get_bucket
    rs = bucket.get_all_keys(headers, maxkeys=0)
  File "/usr/lib/pymodules/python2.6/boto/s3/bucket.py", line 204, in get_all_keys
    headers=headers, query_args=s)
  File "/usr/lib/pymodules/python2.6/boto/s3/connection.py", line 342, in make_request
    data, host, auth_path, sender)
  File "/usr/lib/pymodules/python2.6/boto/connection.py", line 459, in make_request
    return self._mexe(method, path, data, headers, host, sender)
  File "/usr/lib/pymodules/python2.6/boto/connection.py", line 437, in _mexe
    raise e
socket.error: [Errno 110] Connection timed out
failed to upload bundle to lucid-20100515184341/lucid-server-uec-amd64-vmlinuz-virtual.manifest.xml
failed: euca-upload-bundle --bucket lucid-20100515184341 --manifest /tmp/uec-publish-image.Cwu1dq/lucid-server-uec-amd64-vmlinuz-virtual.manifest.xml
Checking bucket: lucid-20100515184341failed to upload kernel

---

### Post by mohammed.ali.eng on 2010-07-19
[COLOR=DarkGreen][SIZE=3][FONT=Comic Sans MS]**same problem here, any updates ??**[/FONT][/SIZE][/COLOR]

> **varunpandeyengg said:**
> I recently installed Ubuntu Enterprise Cloud (UEC) on two of my machines - CC & NC both. I was trying to install the store image through WebUI. I was able to download Ubuntu 9.10 - Karmic Koala (i386) image but while installing, it's giving me following error: -
-------------------------------------------------------------------------------------------------------------------------------------------------------------
Command 'euca-upload-bundle' returned status code 1:
Checking bucket: image-store-1269025279
Traceback (most recent call last):
  File "/usr/bin/euca-upload-bundle", line 226, in
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
socket.error: [Errno 110] Connection timed out
------------------------------------------------------------------------------------------------------------------------------------------------------------
 Please Help me with this. Thanks in advance :-)

---

### Post by isitaboat on 2010-10-13
I'm also having the same problem on a fresh install;

> 
Command 'euca-upload-bundle' returned status code 1:
Checking bucket: image-store-1286979181
Traceback (most recent call last):
  File "/usr/bin/euca-upload-bundle", line 231, in <module>
    main()
  File "/usr/bin/euca-upload-bundle", line 214, in main
    bucket_instance = ensure_bucket(conn, bucket, canned_acl)
  File "/usr/bin/euca-upload-bundle", line 87, in ensure_bucket
    bucket_instance = connection.get_bucket(bucket)
  File "/usr/lib/pymodules/python2.6/boto/s3/connection.py", line 275, in get_bucket
    rs = bucket.get_all_keys(headers, maxkeys=0)
  File "/usr/lib/pymodules/python2.6/boto/s3/bucket.py", line 204, in get_all_keys
    headers=headers, query_args=s)
  File "/usr/lib/pymodules/python2.6/boto/s3/connection.py", line 342, in make_request
    data, host, auth_path, sender)
  File "/usr/lib/pymodules/python2.6/boto/connection.py", line 459, in make_request
    return self._mexe(method, path, data, headers, host, sender)
  File "/usr/lib/pymodules/python2.6/boto/connection.py", line 437, in _mexe
    raise e
socket.error: [Errno 110] Connection timed out


---

