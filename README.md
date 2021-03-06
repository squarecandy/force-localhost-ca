# force-localhost-ca

WordPress curl requests (used in [`wp_remote_get`](https://developer.wordpress.org/reference/functions/wp_remote_get/), etc) use an SSL CA cert file in WP Core, not the system PHP default path, or any custom CA you define in `php.ini`.

Use this drop in plugin (easiest in `/wp-content/mu-plugins`) to fix the issue on localhost.

Helpful for compatibility with local SSL certs generated by the [`mkcert`](https://github.com/FiloSottile/mkcert) command.

Just drop this plugin into /wp-content/mu-plugins and add your custom CA file path to your wp-config.php file like this:

```
define( 'CUSTOM_LOCAL_CA_CERT', '/Users/exampleuser/Library/Application Support/mkcert/rootCA.pem' );
```

Three local TLD endings are supported by default: `.local`, `.localhost` and `.test`. If you need additional endings add them to your wp-config.php file like this:

```
define( 'CUSTOM_LOCAL_CA_TLDS',
	array(
		'localhost',
		'mycrazytld',
		'hyperlocal',
	)
);
```

## thanks

Thanks to [@healdev](https://github.com/healdev) and [@Kevinlearynet](https://github.com/Kevinlearynet) for initial code and concept for this fix.
Original thread: https://github.com/FiloSottile/mkcert/issues/165
