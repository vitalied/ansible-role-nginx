Ansible Role for Nginx & Nginx Passenger module
====================

[![Build Status](https://travis-ci.org/vitalied/ansible-role-nginx.svg?branch=master)](https://travis-ci.org/vitalied/ansible-role-nginx)
[![GitHub tag](https://img.shields.io/github/tag/vitalied/ansible-role-nginx.svg)](https://github.com/vitalied/ansible-role-nginx)
[![GitHub license](https://img.shields.io/github/license/vitalied/ansible-role-nginx.svg)](https://github.com/vitalied/ansible-role-nginx/blob/master/LICENSE)
[![Ansible Role](https://img.shields.io/ansible/role/8567.svg)](https://galaxy.ansible.com/vitalied/nginx)

Ansible Role for Nginx & Nginx Passenger module Management.

Requirements
------------

This role require Ansible 2.1 or higher.

This role was designed for Ubuntu Server 14.04+.

Role Variables
--------------

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>parameter</th>
<th>required</th>
<th>default</th>
<th>choices</th>
<th>comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>nginx_worker_processes</td>
<td>yes</td>
<td>auto</td>
<td></td>
<td>This number should be, at maximum, the number of CPU cores on your system.</td>
</tr>
<tr class="even">
<td>nginx_worker_connections</td>
<td>yes</td>
<td>1024</td>
<td></td>
<td>Determines how many clients will be served by each worker process.</td>
</tr>
<tr class="odd">
<td>nginx_multi_accept</td>
<td>yes</td>
<td>on</td>
<td><ul>
<li><code>on</code></li>
<li><code>off</code></li>
</ul></td>
<td>Accept as many connections as possible, after nginx gets notification about a new connection.</td>
</tr>
<tr class="even">
<td>nginx_sendfile</td>
<td>yes</td>
<td>on</td>
<td><ul>
<li><code>on</code></li>
<li><code>off</code></li>
</ul></td>
<td>Sendfile copies data between one FD and other from within the kernel.</td>
</tr>
<tr class="odd">
<td>nginx_tcp_nopush</td>
<td>yes</td>
<td>on</td>
<td><ul>
<li><code>on</code></li>
<li><code>off</code></li>
</ul></td>
<td>Causes nginx to attempt to send its HTTP response head in one packet, instead of using partial frames.</td>
</tr>
<tr class="even">
<td>nginx_tcp_nodelay</td>
<td>yes</td>
<td>on</td>
<td><ul>
<li><code>on</code></li>
<li><code>off</code></li>
</ul></td>
<td>Don't buffer data-sends (disable Nagle algorithm).</td>
</tr>
<tr class="odd">
<td>nginx_keepalive_timeout</td>
<td>yes</td>
<td>65</td>
<td></td>
<td>Timeout for keep-alive connections. Server will close connections after this time.</td>
</tr>
<tr class="even">
<td>nginx_keepalive_requests</td>
<td>yes</td>
<td>500</td>
<td></td>
<td>Number of requests a client can make over the keep-alive connection.</td>
</tr>
<tr class="odd">
<td>nginx_reset_timedout_connection</td>
<td>yes</td>
<td>on</td>
<td><ul>
<li><code>on</code></li>
<li><code>off</code></li>
</ul></td>
<td>Allow the server to close the connection after a client stops responding.</td>
</tr>
<tr class="even">
<td>nginx_client_body_timeout</td>
<td>yes</td>
<td>12</td>
<td></td>
<td>Send the client a "request timed out" if the body is not loaded by this time.</td>
</tr>
<tr class="odd">
<td>nginx_client_header_timeout</td>
<td>yes</td>
<td>12</td>
<td></td>
<td>Send the client a "request timed out" if the header is not loaded by this time.</td>
</tr>
<tr class="even">
<td>nginx_send_timeout</td>
<td>yes</td>
<td>10</td>
<td></td>
<td>If the client stops reading data, free up the stale client connection after this much time.</td>
</tr>
<tr class="odd">
<td>nginx_gzip</td>
<td>yes</td>
<td>on</td>
<td><ul>
<li><code>on</code></li>
<li><code>off</code></li>
</ul></td>
<td>Use gzip compression.</td>
</tr>
<tr class="even">
<td>nginx_gzip_comp_level</td>
<td>yes</td>
<td>6</td>
<td></td>
<td>Gzip compression level.</td>
</tr>
<tr class="odd">
<td>nginx_install_passenger_version</td>
<td>yes</td>
<td>false</td>
<td><ul>
<li><code>false</code></li>
<li><code>true</code></li>
</ul></td>
<td>Install Nginx Passenger module.</td>
</tr>
<tr class="even">
<td>ruby_user</td>
<td>no</td>
<td>deploy</td>
<td></td>
<td>The user under which the Passenger will run.</td>
</tr>
<tr class="odd">
<td>nginx_passenger_max_pool_size</td>
<td>no</td>
<td>8</td>
<td></td>
<td>
The maximum number of application processes that may simultaneously exist.
<br/>
<a href="https://www.phusionpassenger.com/library/config/nginx/reference/#passenger_max_pool_size">
  Configuration reference for Passenger + Nginx
</a>
</td>
</tr>
<tr class="even">
<td>nginx_passenger_min_instances</td>
<td>no</td>
<td>4</td>
<td></td>
<td>
This specifies the minimum number of application processes that should exist for a given application.
<br/>
<a href="https://www.phusionpassenger.com/library/config/nginx/reference/#passenger_min_instances">
  Configuration reference for Passenger + Nginx
</a>
</td>
</tr>
<tr class="odd">
<td>nginx_passenger_max_instances_per_app</td>
<td>no</td>
<td>0</td>
<td></td>
<td>
The maximum number of application processes that may simultaneously exist for a single application.
<br/>
<a href="https://www.phusionpassenger.com/library/config/nginx/reference/#passenger_max_instances_per_app">
  Configuration reference for Passenger + Nginx
</a>
</td>
</tr>
<tr class="even">
<td>nginx_passenger_pool_idle_time</td>
<td>no</td>
<td>0</td>
<td></td>
<td>
The maximum number of seconds that an application process may be idle.
<br/>
<a href="https://www.phusionpassenger.com/library/config/nginx/reference/#passenger_pool_idle_time">
  Configuration reference for Passenger + Nginx
</a>
</td>
</tr>
<tr class="odd">
<td>nginx_passenger_max_preloader_idle_time</td>
<td>no</td>
<td>0</td>
<td></td>
<td>
The maximum number of seconds that an preloader process may be idle.
<br/>
<a href="https://www.phusionpassenger.com/library/config/nginx/reference/#max_preloader_idle_time">
  Configuration reference for Passenger + Nginx
</a>
</td>
</tr>
</tbody>
</table>

Dependencies
------------

No additional role dependencies.

Example Playbook
----------------

    - hosts: all
      roles:
        - role: vitalied.nginx

License
-------

-   Code released under [MIT](https://github.com/vitalied/ansible-role-nginx/blob/master/LICENSE)
-   Docs released under [CC BY 4.0](http://creativecommons.org/licenses/by/4.0/)
