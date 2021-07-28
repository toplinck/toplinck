- 👋 Hi, I’m @toplinck
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
toplinck/toplinck is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
deletions.
 1  Gemfile 
@@ -0,0 +1 @@
./tool/docker/Gemfile
 1  Gemfile.lock 
@@ -0,0 +1 @@
./tool/docker/Gemfile.lock
  20  README.md 
@@ -25,16 +25,24 @@ A tldr version follows:
1. Ensure you have [Bundler](http://bundler.io/) installed; if not install with:<br>
`gem install bundler`

1. Install all dependencies:<br>
1. Install Ruby gems:<br>
`bundle install`
    * On macOS, if you encounter errors while building native Ruby extensions, see [Installing Nokogiri](http://www.nokogiri.org/tutorials/installing_nokogiri.html#mac_os_x) for troubleshooting tips.

1. Install tool for serving locally
(one-time setup):<br>
`npm install -g superstatic`

1. (Optional) If you plan to deploy to a firebase project, install this package (one-time setup):<br>
`npm install -g firebase-tools`

1. Create a branch.

1. Make your changes.

1. Test your changes by serving the site locally:<br>
`bundle exec jekyll serve` (or `jekyll serve -w --force_polling`)
1. Test your changes by serving the site locally. Run either one of these commands:
  - `tool/serve.sh`
  - `bundle exec jekyll serve --incremental --watch --livereload --port 4002`

1. Prior to submitting, run link validation:<br>
`rake checklinks`
@@ -279,17 +287,17 @@ from dartlang.org, we recommend manually running the following.
* Start the localhost Firebase server:
  ```
  superstatic --port 3474
  superstatic --port 4002
  ```
* Run the link checker:
  ```
  linkcheck :3474
  linkcheck :4002
  ```
  Even better, to check that old URLs are correctly redirected:
  ```
  linkcheck :3474 --input-file tool/sitemap.txt
  linkcheck :4002 --input-file tool/sitemap.txt
  ```
  2  _config.yml 
@@ -14,7 +14,7 @@ kramdown:
  input: GFM
  hard_wrap: false

exclude: [example, packages, tool]
exclude: [example, packages, tool, Gemfile*]

plugins:
  - jekyll-redirect-from
  32  tool/serve.sh 
