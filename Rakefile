# encoding: utf-8
require 'rake/extensiontask'
$__WS2812_SKIP_LL = true
require_relative 'lib/ws2812'

spec = Gem::Specification.new do |s|
	s.name = 'ws2812'
	s.platform = Gem::Platform::CURRENT
	s.extensions = FileList["ext/**/extconf.rb"]
	s.version = Ws2812::VERSION
	s.date = '2015-04-16'
	s.summary = 'Ruby wrapper around WS2812 LED driver for Raspberry Pi'
	s.description = 'Gem that encapsulates modified RaspberryPi-NeoPixel-WS2812 library from UnicornHat to help drive your WS2812 led chain from RaspberryPi'
	s.authors = ['Michal Jirků']
	s.email = 'box@wejn.org'
	s.files = `git ls-files -z`.split("\x0")
	s.homepage = 'https://rubygems.org/gem/ws2812'
	s.license = 'GPL'
	s.add_development_dependency "rake"
	s.add_development_dependency "rake-compiler"
end

Gem::PackageTask.new(spec) do |pkg|
end

Rake::ExtensionTask.new "ws2812" do |ext|
	ext.name = 'lowlevel'
	ext.ext_dir = 'ext/ws2812'
	ext.lib_dir = 'lib/ws2812'
	ext.gem_spec = spec
end

task :clobber => :clobber_extras
task :clobber_extras do
	Dir.chdir('ext/ws2812/lib') do
		system('make', 'clean')
	end
end
