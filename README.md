# SSL Management - Hostinger and Let's Encrypt

Updated: 8 Novmeber 2021

How to Create and Manage SSL Certs with Let's Encrypt on your Mac to install on Hostinger for shared server static web content.

To install the cert on Hostinger you will need access to the .well-know directory in the public_html directory of your domain.  Right now I beleive the only way to get this to work is to point your DNS record to Hostinger DNS servers:  
Hostinger Name Servers
|---------------------
| ns1.dns-parking.com
| ns2.dns-parking.com

Install certbot - You made need to install xcode command line tools
```
brew install certbot
```

Note: To run brew you will need to install brew and the Apple xCode tools on your Mac

To install brew do the following:
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Run certbot for certifcate only in manual mode
```
sudo certbot certonly --manual
```
When generating the key for each domain, don't forget to specifiy both the domain name and FQDN.  Ex. www.bob.com and bob.com

Certbot with then tell you the file name and file contents to place in the .well-know/acme-challenge directory.  Do not presse the enter key until you have set this up on your target domain.  

If you certbot can correctly access the file, it will generate the necessary keys for your SSL cert and tell you which directory they are stored in.  Add the following keys to the text fields listed on hostinger's Install SSL page.
Certbot Key | Hostinger Field
----------- | ---------------
cert.pem | Cert Key
privkey.pem | Private Key
chain.pem | CABUNDLE
