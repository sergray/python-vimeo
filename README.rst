This a Python library implementing a client for `Advanced Vimeo API <https://developer.vimeo.com/apis/advanced/methods>`_.

Installation
------------

Regular python distutils::

	$ python setup.py install prefix=/somewhere/in/the/universe

You can also create debian package::

	$ dpkg-buildpackage


Usage
-----

Obtain oAuth keys/tokens from https://developer.vimeo.com/apps and
start your favorite Python shell::

	from vimeo import VimeoClient
	client = VimeoClient(key=key, secret=secret, format='json')
	client.get_request_token()
	print "Open in browser", client.get_authorization_url(permission="write")
	verifier = raw_input('Copy&paste oAuth verifier from the URL: ')
	client.set_verifier(verifier)
	token = client.get_access_token()
	all_videos = client.vimeo_videos_getAll()
	upload_quota = client.vimeo_videos_upload_getQuota()

`VimeoClient` methods for accessing API are dynamically resolved.
Sorry, no methods introspection and builtin documentation so far.
Underscore corresponds to the dot in Vimeo API documentation, e.g. 
`vimeo.videos.getAll` becomes a `vimeo_videos_getAll` client method.

Simple video uploading with POST API is somewhat supported too, see vimeo-uploadv2.py and vimeo-query.py script for more details.


Contributors
------------

Thanks :)

- mishk (for the 99% patch that reduced amazingly the code while still improving it greatly!)
- Bengt Sjölén
- Okke Formsma
- "aseppala" on github
