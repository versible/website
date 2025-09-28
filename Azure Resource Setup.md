# Azure Content Delivery Network
Seems like you can't expose Storage Static Website to a custom domain with HTTPS support.

## Set up a CDN
To set up a CDN, first need to register CDN Resources for use with the VersibleProd subscription.  
Subscription --> Settings --> Resource providers.  Find Microsoft.cdn and Register (takes several minutes).

## Create a CDN Endpoint
https://learn.microsoft.com/en-us/azure/cdn/cdn-create-new-endpoint

New Resource called "Front Door and CDN profiles".  Explore other offerings.  Azure CDN Standard from Microsoft (classic).

* Resource group, create new.  CDNVersible-rg
* EUW
* Name CDN-profile-versible
* Pricing tier Microsoft Standard

Add an endpoint
* Name cdn-endpoint-versible
* Origin type: Storage Static Website
* Everything else default

Edit GoDaddy CNAME DNS to add www pointing to cdn-endpoint-versible.azureedge.net

On the Endpoint, custom domain HTTPS needs turning on.  CDN Managed with TLS 1.2.  See https://learn.microsoft.com/en-us/azure/cdn/cdn-custom-ssl?tabs=option-1-default-enable-https-with-a-cdn-managed-certificate
