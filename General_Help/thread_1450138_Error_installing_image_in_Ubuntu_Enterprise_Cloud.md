---
title: "Error installing image in Ubuntu Enterprise Cloud"
date: 2010-04-08
forum: General Help
---

### Post by elikary on 2010-04-08
I'm trying to install the image: Ubuntu 9.10 - Karmic Koala  (i386) by the web interface, but it returns that error

I'm using ubuntu enterprise cloud 9.10




 Command 'euca-upload-bundle' returned status code 1:
Checking bucket: image-store-1270758678
Traceback (most recent call last):
  File "/usr/bin/euca-upload-bundle", line 226, in
    main()
  File "/usr/bin/euca-upload-bundle", line 209, in main
    bucket_instance = ensure_bucket(conn, bucket, canned_acl)
  File "/usr/bin/euca-upload-bundle", line 87, in ensure_bucket
    bucket_instance = connection.get_bucket(bucket)
  File "/usr/lib/pymodules/python2.6/boto/s3/connection.py", line 238,  in get_bucket
    rs = bucket.get_all_keys(None, maxkeys=0)
  File "/usr/lib/pymodules/python2.6/boto/s3/bucket.py", line 204, in  get_all_keys
    headers=headers, query_args=s)
  File "/usr/lib/pymodules/python2.6/boto/s3/connection.py", line 305,  in make_request
    data, host, auth_path, sender)
  File "/usr/lib/pymodules/python2.6/boto/connection.py", line 419, in  make_request
    return self._mexe(method, path, data, headers, host, sender)
  File "/usr/lib/pymodules/python2.6/boto/connection.py", line 398, in  _mexe
    raise e
socket.error: [Errno 113] No route to host






 please help me

---

