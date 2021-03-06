# WebService::Xero


[![Build Status](https://travis-ci.org/pscott-au/CCP-Xero.svg?branch=master)](https://travis-ci.org/pscott-au/CCP-Xero)
[![Coverage Status](https://coveralls.io/repos/github/pscott-au/CCP-Xero/badge.svg?branch=master)](https://coveralls.io/github/pscott-au/CCP-Xero?branch=master)
[![CPAN Version](https://img.shields.io/cpan/v/WebService-Xero.svg)](http://search.cpan.org/~localshop/WebService-Xero/lib/WebService/Xero.pm)
[![Join the chat at https://gitter.im/CCP-AU/](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/CCP-AU?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badgeP-AU/Lobby?source=orgpage)

Perl CPAN style module to simplify integration with [Xero API Applications](https://developer.xero.com)

Inspired by the Xero endorsed Ruby API Library [Xeroizer] 
and the CPAN [Net::Xero](http://search.cpan.org/~elliott/Net-Xero/lib/Net/Xero.pm) module, this Perl module aims to simplify integration with Xero API Applications
points for Public, Private and in the future Partner application services.
WebService::Xero modules primarily encapsulate the [OAuth (v1.0a) access control protocol as described by Cubrid](http://www.cubrid.org/blog/dev-platform/dancing-with-oauth-understanding-how-authorization-works/) .


This package is now available through [CPAN](http://search.cpan.org/~localshop/WebService-Xero/)

## Prerequisites 

* Perl
* build tools ( make etc )
* Xero API Application with credentials as descibed in the [Xero Developer Getting Started Guide](https://developer.xero.com/documentation/getting-started/getting-started-guide/)

````sh
sudo apt-get install perl build-essential ## eg debian package install
````

## Installing Manually


This Perl code is in the standard CPAN package format and can be installed through CPAN or downloaded and installed manually either from GitHub or CPAN:

```sh
  perl Makefile.PL
  make
  make test
  make install
```

### Installing Step by Step

Download the latest stable source:

```sh
    git clone https://github.com/Combined-Computer-Professionals/WebService-Xero
    cd WebService-Xero
```

Create the makefile

```sh
perl Makefile.PL
```
If given notice of missing dependency modules, these can be installed from CPAN. For example to install a missing Crypt::OpenSSL::RSA module:
```sh
    sudo perl -MCPAN -e "install Crypt::OpenSSL::RSA"
    ## or if you have cpanm installed
    cpanm --installdeps .
```

NB: Crypt::OpenSSL::RSA from CPAN requires SSL devel libraries which
    can be installed as follows:
```sh 
  apt-get install libssl-dev   ## for debian etc
  yum install openssl-devel    ## for RH,Centos, Ubuntu etc
```
Make,test and install the library
```sh
make
make test
make install
```

## Usage

An example of a basic agent accessing a private Xero Application.
````perl
#!/usr/bin/perl
use strict;
use warnings;
use WebService::Xero::Agent::PrivateApplication;
use Data::Dumper;

my $xero = WebService::Xero::Agent::PrivateApplication->new( CONSUMER_KEY    => 'YOUR_OAUTH_CONSUMER_KEY', 
                                                    CONSUMER_SECRET => 'YOUR_OAUTH_CONSUMER_SECRET', 
                                                    PRIVATE_KEY      => '-----BEGIN RSA PRIVATE KEY-----.....etc'
                                                          );
## AND THEN ACCESS THE XERO API POINTS

my $contact_struct = $xero->do_xero_api_call( 'https://api.xero.com/api.xro/2.0/Contacts' );
print Dumper $contact_struct; ## should contain an array of hashes containing contact data.
````

An example of a minimalistic Mojolicious framework Public Application implementation can be found at [github.com/pscott-au/mojolicious-xero-public-app-demo](https://github.com/pscott-au/mojolicious-xero-public-app-demo)

See perldoc for details
````sh
perldoc WebService::Xero
````

### Todos

 - Classes for all Xero Components ( Item, Contact, Invoice etc )
 - Working Public Application Example 
 - Partner Application Interface

LICENSE AND COPYRIGHT
----

Copyright 2016 Peter Scott.

This program is free software; you can redistribute it and/or modify it
under the terms of the the Artistic License (2.0). You may obtain a
copy of the full license at:

http://www.perlfoundation.org/artistic_license_2_0

Any use, modification, and distribution of the Standard or Modified
Versions is governed by this Artistic License. By using, modifying or
distributing the Package, you accept this license. Do not use, modify,
or distribute the Package, if you do not accept this license.

If your Modified Version has been derived from a Modified Version made
by someone other than you, you are nevertheless required to ensure that
your Modified Version complies with the requirements of this license.

This license does not grant you the right to use any trademark, service
mark, tradename, or logo of the Copyright Holder.

This license includes the non-exclusive, worldwide, free-of-charge
patent license to make, have made, use, offer to sell, sell, import and
otherwise transfer the Package with respect to any patent claims
licensable by the Copyright Holder that are necessarily infringed by the
Package. If you institute patent litigation (including a cross-claim or
counterclaim) against any party alleging that the Package constitutes
direct or contributory patent infringement, then this Artistic License
to you shall terminate on the date that such litigation is filed.

Disclaimer of Warranty: THE PACKAGE IS PROVIDED BY THE COPYRIGHT HOLDER
AND CONTRIBUTORS "AS IS' AND WITHOUT ANY EXPRESS OR IMPLIED WARRANTIES.
THE IMPLIED WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR
PURPOSE, OR NON-INFRINGEMENT ARE DISCLAIMED TO THE EXTENT PERMITTED BY
YOUR LOCAL LAW. UNLESS REQUIRED BY LAW, NO COPYRIGHT HOLDER OR
CONTRIBUTOR WILL BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, OR
CONSEQUENTIAL DAMAGES ARISING IN ANY WAY OUT OF THE USE OF THE PACKAGE,
EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.


### Development Support

Want to contribute? Great, get in touch!
Need some help with your setup - will try to help where I can.


[Xeroizer]: <https://github.com/waynerobinson/xeroizer/README.md>
  

