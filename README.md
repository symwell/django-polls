# Reproduce AppMapp error in Django

Setup

1. Download and setup
    1. pipenv install django
    2. pipenv install appmap
    3. python manage.py migrate
    4. pipenv shell

-------------

Trying to run tests the Django way

1. run `APPMAP=true python manage.py test`
2. Open the Appmap extension in VS code and note that there are only `record_requests` in APPMAPS

-------------

How about running tests with unittest instead of Django?

1. run `APPMAP=true python -m unittest -v polls.tests`
2. Note the error `django.core.exceptions.AppRegistryNotReady: Apps aren't loaded yet.`

-------------

How about using appmap.unittest.TestCase?

1. Switch to branch `appmap-testcase`
2. run `APPMAP=true python manage.py test`
3. Note the error `AttributeError: type object '_FailedTest' has no attribute 'tests'`
4. run `APPMAP=true python -m unittest -v polls.tests`
5. Note same error
