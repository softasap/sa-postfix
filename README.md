sa-postfix
==========

[![Build Status](https://travis-ci.org/softasap/sa-postfix.svg?branch=master)](https://travis-ci.org/softasap/sa-postfix)


Example of use: check box-example

Simple:

```YAML


     - {
         role: "sa-postfix",
         postfix_hostname: "appserver.example.com"
       }

```


Advanced:

```YAML


     - {
         role: "sa-postfix",
         postfix_hostname: "appserver.example.com",
         postfix_null_client_properties:
           - {regexp: "^myhostname =*", line: "myhostname = {{postfix_hostname}}"}
           - {regexp: "^myorigin =*", line: "myorigin = $mydomain"}
           - {regexp: "^relayhost =*", line: "relayhost = $mydomain"}
           - {regexp: "^inet_interfaces =*", line: "inet_interfaces = loopback-only"}
           - {regexp: "^mydestination =*", line: "mydestination = loopback-only"}
       }

```


# Misc hints

To check, it actually sends - check

```shell

echo "This is the body of the email" | mail -s "This is the subject line" your_email_address

```

Note, that by default you have major chances, that sent mail will finish it's line in SPAM.  Configuring your MTA & DNS is out of scope for this role.


Copyright and license
---------------------

Copyright - Vyacheslav Voronenko

Code licensed under the [BSD 3 clause] (https://opensource.org/licenses/BSD-3-Clause) or the [MIT License] (http://opensource.org/licenses/MIT).

Subscribe for roles updates at [FB] (https://www.facebook.com/SoftAsap/)
