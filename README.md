# Unifi USG config for ByTel FTTH

![USG3](https://github-assets.meleia.net/images/unifi/USG3.png "USG3") ![ByTel logo](https://github-assets.meleia.net/images/unifi/bytel.png "ByTel Logo")

If you want to use a Unifi USG3 instead of the BBox used on Bouygues Telecom FTTH contracts, here's some things you need to know (this is only for internet, no TV, no phone). Bouygues Telecom uses VLAN 200 for internet access through DHCP when directly connected to the GPON ONT. It also requires some `client-option` to be set to `send vendor-class-identifier "byteliad_data"`.

This is a basic Unifi config to use with [Ubiquiti Unifi USG](https://www.ubnt.com/unifi-routing/usg/) and [Bouygues Telecom FTTH](https://www.bouyguestelecom.fr/offres-internet/internet-fibre-ftth).

It does include some basic SNMP settings for external monitoring with:

- community name (change with your own details)  
- authorization = ro
- client ip restriction (change with your own details)

Also includes firewall rule to allow snmp on `WAN_LOCAL`.

You need to put this file in the following path:

- On a Unifi Cloud Key:  
	`/srv/unifi/data/[site name/default]/`

- If you're using a Raspberry Pi or any other Linux device:  
	`/usr/lib/unifi/data/sites/[site name/default]/`

- On macOS:  
	`/Applications/UniFi.app/Contents/Resources/`  
	_TIP: do not double click on UniFi.app, as it will launch the application, instead, right click > Show Package Contents._  

- On Windows:  
	`"%userprofile%/Ubiquiti Unifi/"`

An easy way to test the validity of the json file is: `python -m json.tool config.gateway.json`

Once added, be sure to trigger a `FORCE PROVISION` from within the Unifi Controller.

![Force Provision](https://github-assets.meleia.net/images/unifi/provision.png "Force Provision")
