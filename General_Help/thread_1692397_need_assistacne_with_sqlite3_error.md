---
title: "need assistacne with sqlite3 error"
date: 2011-02-21
forum: General Help
---

### Post by JMatlack on 2011-02-21
Can you help me by explaining where the database file should go and why? I dont know what path to put in settings.py for ubuntu. On windows I can use 
]import os
PROJECT_ROOT = os.path.abspath(os.path.dirname(__file__))
 
 
 
my settings.py database name= os.path.join(PROJECT_ROOT, 'cms.db')
 
 
for saome reason it tells me that file is undefined
This is the traceback I get
> josh@optimus-prime:~/django-projects/mysite$ python manage.py syncdb
Traceback (most recent call last):
File "manage.py", line 11, in <module>
execute_manager(settings)
File "/usr/local/lib/python2.5/site-packages/django/core/management/__init__.py", line 362, in execute_manager
utility.execute()
File "/usr/local/lib/python2.5/site-packages/django/core/management/__init__.py", line 303, in execute
self.fetch_command(subcommand).run_from_argv(self.argv)
File "/usr/local/lib/python2.5/site-packages/django/core/management/base.py", line 195, in run_from_argv
self.execute(*args, **options.__dict__)
File "/usr/local/lib/python2.5/site-packages/django/core/management/base.py", line 221, in execute
self.validate()
File "/usr/local/lib/python2.5/site-packages/django/core/management/base.py", line 249, in validate
num_errors = get_validation_errors(s, app)
File "/usr/local/lib/python2.5/site-packages/django/core/management/validation.py", line 22, in get_validation_errors
from django.db import models, connection
File "/usr/local/lib/python2.5/site-packages/django/db/__init__.py", line 41, in <module>
backend = load_backend(settings.DATABASE_ENGINE)
File "/usr/local/lib/python2.5/site-packages/django/db/__init__.py", line 17, in load_backend
return import_module('.base', 'django.db.backends.%s' % backend_name)
File "/usr/local/lib/python2.5/site-packages/django/utils/importlib.py", line 35, in import_module
__import__(name)
File "/usr/local/lib/python2.5/site-packages/django/db/backends/sqlite3/base.py", line 32, in <module>
raise ImproperlyConfigured, "Error loading %s: %s" % (module, exc)
django.core.exceptions.ImproperlyConfigured: Error loading either pysqlite2 or sqlite3 modules (tried in that order): No module named _sqlite3
josh@optimus-prime:~/django-projects/mysite$ 

grateful for any help thanks

---

