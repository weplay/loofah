require 'rubygems'
gem 'hoe', '>= 2.3.0'
require 'hoe'

Hoe.plugin :git

Hoe.spec "loofah" do
  developer "Mike Dalessio", "mike.dalessio@gmail.com"
  developer "Bryan Helmkamp", "bryan@brynary.com"

  self.extra_rdoc_files = FileList["*.rdoc"]
  self.history_file     = "CHANGELOG.rdoc"
  self.readme_file      = "README.rdoc"

  extra_deps << ["nokogiri", ">= 1.3.3"]

  # note: .hoerc should have the following line to omit rails tests and tmp
  #   exclude: !ruby/regexp /\/tmp\/|\/rails_tests\/|CVS|TAGS|\.(svn|git|DS_Store)/
end

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "loofah"
    gem.summary = %Q{HTML sanitization}
    gem.description = %Q{Loofah is an HTML sanitizer. It will always fix broken markup, but can also sanitize unsafe tags in a few different ways, and transform the markup for storage or display.}
    gem.email = "tech@weplay.com"
    gem.homepage = "http://github.com/weplay/loofah"
    gem.authors = ["Bryan Helmkamp", "Mike Dalessio"]
    gem.add_dependency 'nokogiri', '>= 1.3.3'
  end
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: gem install jeweler"
end


if File.exist?("rails_test/Rakefile")
  load "rails_test/Rakefile"
else
  task :test do
    puts "----------"
    puts "-- NOTE: An additional Rails regression test suite is available in source repository"
    puts "----------"
  end
end

task :redocs => :fix_css
task :docs => :fix_css
task :fix_css do
  better_css = <<-EOT
.method-description pre {
  margin: 1em 0 ;
}

.method-description ul {
  padding: .5em 0 .5em 2em ;
}

.method-description p {
  margin-top: .5em ;
}

div#main ul {
  list-style-type: disc ;
  list-style-position: inside ;
}
EOT
  puts "* fixing css"
  File.open("doc/rdoc.css", "a") { |f| f.write better_css }
end

