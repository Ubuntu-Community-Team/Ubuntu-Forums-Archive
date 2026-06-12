---
title: "gdatacopier stopped working on update"
date: 2012-05-23
forum: General Help
---

### Post by yairsuari on 2012-05-23
hello.
i just updated to 11.04 (late) a script i was using to download data from google docs stopped working, cant tell the reason.
i am using gdatacopier which is using in turn googlecl in this fashion:

i am not even able to use gcp

gcp.py  -o [email]MyUserName@gmail.com[/email]:/sheets/1/A1_database /tmp  -f csv --password *********

it worked perfectly 2 weeks ago but now i am getting the following error (i think its coming from gdata)



 Fetching document list feeds from Google servers for [email]MyUserName@gmail.com[/email] ... Traceback (most recent call last):
  File "./gcp.py", line 541, in <module>
    main()
  File "./gcp.py", line 537, in main
    parse_user_input()			# Check to see we have the right options or exit
  File "./gcp.py", line 519, in parse_user_input
    export_documents(document_source, document_target, options)
  File "./gcp.py", line 199, in export_documents
    feed = gd_client.Query(document_query.ToUri())
  File "/usr/lib/pymodules/python2.7/gdata/docs/service.py", line 217, in Query
    return self.Get(uri, converter=converter)
  File "/usr/lib/pymodules/python2.7/gdata/service.py", line 1102, in Get
    'reason': server_response.reason, 'body': result_body}
gdata.service.RequestError: {'status': 403, 'body': '403.4 SSL required', 'reason': 'Forbidden'}

---

